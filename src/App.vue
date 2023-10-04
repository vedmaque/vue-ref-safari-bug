<script setup>
import hljs from 'highlight.js/lib/core';
import javascript from 'highlight.js/lib/languages/javascript';
import 'highlight.js/styles/atom-one-dark.css'
import { ref, computed } from 'vue'

hljs.registerLanguage('javascript', javascript)

const obj = ref({0: 'a', 1: 'b', 2: 'c'})

const objValues1 = computed(() => Object.values(obj.value))
const sourceCode = `import { ref, computed } from 'vue'

const obj = ref({0: 'a', 1: 'b', 2: 'c'});

const objValues = computed(() => Object.values(obj.value));`

const code = hljs.highlight(sourceCode, {language: 'javascript'}).value
</script>

<template>
  <div class="app">
    <div>
      <p>Source code:</p>
      <pre><code class="hljs" v-html="code"></code></pre>
      <div>
        <table>
          <tr>
            <td>obj:</td>
            <td>{{ obj }}</td>
          </tr>
          <tr>
            <td>Object.values(obj):</td>
            <td>{{ objValues1 }}</td>
          </tr>
          <tr>
            <td>Expected result:</td>
            <td>[ "a", "b", "c" ]</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<style>
body {
  font-family: -apple-system, -apple-system, 
                BlinkMacSystemFont, 'Segoe UI', Roboto, 
                Oxygen, Ubuntu, Cantarell, 'Open Sans', 
                'Helvetica Neue', sans-serif;
}

.app {
  display: flex;
  justify-content: center;
}
</style>
