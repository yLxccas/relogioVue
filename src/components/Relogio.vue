<template>
  <div class="container">
    <div class="cardClock">

      <div class="cardNumber">
        <span id="hours">{{ hours }}</span>
        <span class="time">{{msg.hours}}</span>
      </div>

      <div class="cardNumber">
        <span id="minutes">{{ minutes }}</span>
        <span class="time">{{msg.minutes}}</span>
      </div>

      <div class="cardNumber">
        <span id="seconds">{{ seconds }}</span>
        <span class="time">{{msg.seconds}}</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";

const msg = {
  hours: "Horas",
  minutes: "Minutos",
  seconds: "Segundos"
};

const hours = ref("00");
const minutes = ref("00");
const seconds = ref("00");

function setTime() {
  const date = new Date();
  hours.value = date.getHours().toString().padStart(2, "0");
  minutes.value = date.getMinutes().toString().padStart(2, "0");
  seconds.value = date.getSeconds().toString().padStart(2, "0");
}

onMounted(() => {
  setInterval(() => setTime(), 1000);
});
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;500&display=swap');

* {
  margin: 0;
  padding: 0;
  font-family: 'Open Sans', sans-serif;
}

.container {
  height: 100vh;
  width: 100vw;
  background: linear-gradient(150deg, #f8f16f, #ff0000);
  display: flex;
  align-items: center;
  justify-content: center;
}

.cardClock {
  display: flex;
  align-items: center;
  justify-content: space-around;
  height: 200px;
  width: 550px;
  background: transparent;
  border-radius: 3px;
  box-shadow: 0px 8px 10px rgba(0, 0, 0, .5);
}

.cardNumber {
  height: 170px;
  width: 150px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: #fff;
  background: rgba(5, 5, 5, .9);
  box-shadow: 5px 5px 15px rgba(0, 0, 0, .7);
  border-radius: 7px;
  letter-spacing: 3px;
}

.cardNumber span {
  font-weight: bold;
  font-size: 60px;
}

.cardNumber span.time {
  font-size: 10px;
}
</style>