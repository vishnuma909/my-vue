<template>
  <div>
    <h1>{{ dashboard }}</h1>
    <v-form v-model="valid">
      <div
        label="testing"
      >{{ inputFieldText }}</div>
      <v-btn
        elevation="2"
        outlined
        raised
        @click="changeText()"
      >Change input</v-btn>
    </v-form>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

// empty components is to satisfy vuetify to install its components once rendered
@Component({
  components: {}
})
export default class Dashboard extends Vue {
  dashboard = "Dashboard";

  inputFieldText: string = "This is Dashboard";
  valid: boolean = true;

  // function to check beforeUpdate, updated, updated with $nextTick events triggering
  changeText() {
    this.inputFieldText = "Hi changed text";
  }

  // life cycle hooks
  /**
   * Called synchronously immediately after the instance has been initialized
   * before data observation and event/watcher setup.
   */
  beforeCreate() {
    console.log(`before create`);
  }

  /**
   * Called synchronously after the instance is created
   * at this stage, the instance has finished processing the options
   */
  created() {
    console.log(`created`);
  }

  /**
   * Called right before the mounting begins: the render function is about to be called for the first time.
   * This hook is not called during server-side rendering.
   */
  beforeMount() {
    console.log(`before mount`);
  }

  /**
   * Called after the instance has been mounted,
   * where el is replaced by the newly created vm.$el
   */
  mounted() {
    console.log(`mounted`);
    /**
     * this code that will run only after the
     * entire view has been rendered
     */
    this.$nextTick(() => console.log(`mounted: all child mounted`));
    // this.$nextTick(() => console.log(`mounted: all child mounted`));
  }

  /**
   * when any data changes its state value
   * This hook is not called during server-side rendering,
   * because only the initial render is performed server-side.
   */
  beforeUpdate() {
    console.log(`before update`);
  }

  // Called after a data change causes the virtual DOM to be re-rendered and patched.
  updated() {
    console.log(`updated`);
    /**
     * this code that will run only after the
     * entire view has been rendered
     */
    this.$nextTick(() => console.log(`updated: all child mounted`));
  }

  // Called right before a Vue instance is destroyed. At this stage the instance is still fully functional.
  beforeDestroy() {
    console.log(`before destroy`);
  }

  // Called after a Vue instance has been destroyed.
  destroyed() {
    console.log(`destroyed`);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
