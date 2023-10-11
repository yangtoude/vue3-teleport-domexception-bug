<template>
  <main>
    <!-- v-show will works fine, but v-if will throw error -->
    <div v-if="showContent === true">
      <button
        @click="handleToAbout"
      >to about</button>
      <div>open console, when click "to about" will throw error</div>
      <!-- to="#app" will throw error below -->
      <!-- Uncaught (in promise) DOMException: Failed to execute 'insertBefore' on 'Node': The node before which the new node is to be inserted is not a child of this node. -->
      <teleport
        to="#app"
      >
        <div style="background-color: lightblue;">teleport to app</div>
      </teleport>

      <!-- to="body" works fine -->
      <!-- <teleport
        to="body"
      >
        <div style="background-color: lightcoral;">teleport to body</div>
      </teleport> -->
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useRouter } from 'vue-router';
const showContent = ref<boolean|null>(false)

setTimeout(() => {
  showContent.value = true
}, 100)

const router = useRouter()
const handleToAbout = () => {
  router.push({
    path: '/about'
  })
}

</script>
