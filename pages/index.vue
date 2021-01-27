<template>
  <div class="container">
    <vue-selecto
      drag-container=".elements"
      :selectable-targets="['.selecto-area .cube']"
      :hit-rate="10"
      :select-by-click="true"
      :select-from-inside="false"
      :ratio="0"
      @select="onSelect"
    ></vue-selecto>
    <div id="selecto1" class="elements selecto-area">
      <div v-for="(cube, index) in cubes" :key="index" class="cube"></div>
    </div>
  </div>
</template>

<script>
import { VueSelecto } from 'vue-selecto'
export default {
  components: {
    VueSelecto,
  },
  data() {
    const cubes = []

    for (let i = 0; i < 60; ++i) {
      cubes.push(i)
    }
    return {
      cubes,
    }
  },
  methods: {
    onSelect(e) {
      console.log(e)
      e.added.forEach((el) => {
        console.log(el)
        el.classList.add('selected')
      })
      e.removed.forEach((el) => {
        console.log(el)
        el.classList.remove('selected')
      })
    },
  },
}
</script>

<style>
html,
body,
#root {
  position: relative;
  margin: 0;
  padding: 0;
  color: #333;
  background: #fdfdfd;
}

.container {
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: center;
}

.app {
  position: relative;
  padding: 10px 20px;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
}

.container {
  max-width: 800px;
}

body {
  background: #fff;
}

.logo {
  position: relative;
  width: 150px;
  height: 150px;
  margin: 0px auto;
  font-size: 0;
  text-align: left;
}

.logo.logos {
  width: 320px;
  text-align: center;
}

.logos .selecto {
  padding: 16px;
}

.logo img {
  position: relative;
  height: 100%;
  box-sizing: border-box;
}

.cube {
  display: inline-block;
  border-radius: 5px;
  width: 40px;
  height: 40px;
  margin: 4px;
  background: #eee;
  --color: #4af;
}

h1,
.description {
  text-align: center;
}

.button {
  border: 1px solid #333;
  color: #333;
  background: transparent;
  appearance: none;
  -webkit-appearance: none;
  box-sizing: border-box;
  cursor: pointer;
  width: 120px;
  height: 42px;
  font-size: 14px;
  letter-spacing: 1px;
  transition: all ease 0.2s;
  margin: 0px 5px;
}

.button:hover {
  background: #333;
  color: white;
}

.elements {
  margin-top: 40px;
  border: 2px solid #eee;
}

.selecto-area {
  padding: 20px;
}

#selecto1 .cube {
  transition: all ease 0.2s;
}

.moveable #selecto1 .cube {
  transition: none;
}

.selecto-area .selected {
  color: #fff;
  background: var(--color);
}

.scroll {
  overflow: auto;
  padding-top: 10px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.infinite-viewer,
.scroll {
  width: 100%;
  height: 300px;
  box-sizing: border-box;
}

.infinite-viewer .viewport {
  padding-top: 10px;
}

.empty.elements {
  border: none;
}
</style>
