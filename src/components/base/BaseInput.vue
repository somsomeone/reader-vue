<template>
  <div class="form-group row">
    <label v-if="label">{{ label }}</label>
    <input :value="value" class="form-control" v-bind="$attrs" v-on="listeners" />
  </div>
</template>

<script>
export default {
  inheritAttrs: false,
  props: {
    label: {
      type: String,
      default: ""
    },
    value: [String, Number]
  },
  methods: {
    updateValue(event) {
      this.$emit("input", event.target.value);
    }
  },
  computed: {
    listeners() {
      return {
        ...this.$listeners,
        input: this.updateValue
      };
    }
  }
};
</script>

<style>
</style>