<template>
  <div
    draggable
    @dragstart.self="onDrag"
    @dragover.prevent
    @dragenter.prevent
  >
    <slot />
  </div>
</template>

<script>
export default {
  props: {
    transferData: {
      type: Object,
      required: true
    }
  },
  methods: {
    onDrag (e) {
      e.dataTransfer.effectAllow = 'move'
      e.dataTransfer.dropAllow = 'move'

      e.dataTransfer.setData('payload', JSON.stringify(this.transferData))
    }
  }
}
</script>

<style>

</style>
