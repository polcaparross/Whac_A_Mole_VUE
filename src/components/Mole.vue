<script>
import empty from '../empty.png'
import mole from '../mole.png'
import ouch from '../ouch.png'
export default {
  data() {
    return {
      name: 'Mole',
      actual: empty,
      alive: true,
      eliminated: false
    }
  },
  created() {
    this.startInterval()
  },
  methods: {
    startInterval() {
      setInterval(() => {
        if (!this.eliminated) {
          if (this.actual == mole) {
            this.actual = empty
          } else {
            this.actual = mole
          }
        }
      }, Math.random() * 1000 + 500)
    },
    matar() {
      if (this.actual == mole) {
        this.actual = ouch
        this.eliminated = true
      }
    }
  }
}
</script>

<template>
  <div class="moleHole" id="mole" @click="matar()">
    <img :src=actual>
  </div>
</template>


<style>
.moleHole {
  border: solid 1px black;
  margin: 2px;
}
</style>
