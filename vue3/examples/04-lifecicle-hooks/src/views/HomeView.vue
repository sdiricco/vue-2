<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>

    <h3>{{ counterData.title }}:</h3>

    <div>
      <button @click="decreaseCounter(2)" class="btn">--</button>
      <button @click="decreaseCounter(1)" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1, $event)" class="btn">+</button>
      <button @click="increaseCounter(2)" class="btn">++</button>
    </div>

    <p>This counter is {{ oddOrEven }}</p>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text" />
    </div>
  </div>
</template>

<script setup>

/* imports */ 

import {
  reactive,
  computed,
  watch,
  onBeforeMount,
  onMounted,
  onBeforeUnmount,
  onUnmounted,
  onUpdated,
  onBeforeUpdate,
  onActivated,
  onDeactivated,
  onErrorCaptured,
} from "vue";

/* app title */

const appTitle = "My Ok Counter App";

onMounted(() => {
  console.log("Do stuff related to App Title");
});

/* counter */

const counterData = reactive({
  count: 0,
  title: "My Counter",
});

watch(
  () => counterData.count,
  (newCount) => {
    if (newCount === 20) {
      alert("Way to go! You made it to 20!!");
    }
  }
);

const oddOrEven = computed(() => {
  if (counterData.count % 2 === 0) return "even";
  return "odd";
});

const increaseCounter = (amount, e) => {
  counterData.count += amount;
};

const decreaseCounter = (amount) => {
  counterData.count -= amount;
};

onMounted(() => {
  console.log("Do stuff related to Counter");
});

/**
 * All lifecicle hooks
 *
 * onBeforeMount, onMounted, onUnmounted, onUpdated, onBeforeUpdate, onActivated, onDeactivated, onErrorCaptured
 */

onBeforeMount(() => {}),
  onMounted(() => {}),
  onBeforeUnmount(() => {}),
  onUnmounted(() => {}),
  onUpdated(() => {}),
  onBeforeUpdate(() => {}),
  onActivated(() => {}),
  onDeactivated(() => {});
onErrorCaptured(() => {});
</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn,
.counter {
  font-size: 40px;
  margin: 10px;
}
.edit {
  margin-top: 60px;
}
</style>
