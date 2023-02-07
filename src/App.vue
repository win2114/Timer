<script setup>
import { ref } from 'vue';
let blick = ref('')
const text = "alumilize"
let score = text.length
let timer = 30
let func = (event) => {
    const key = event.key;
    console.log(key);
    // blick.value+=key //ใส่+=เพราะเมื่อรับค่าจะคีย์บอร์ดจะใส่แค่เท่ากับมันจะเปลี่ยนไปเรื่อยๆแต่ไม่รับค่า
    if (key !== 'Backspace') {blick.value+=key}
    if(key === 'Backspace'){blick.value = blick.value.slice(0,-1)}
    // if(blick.length === text.length){window.removeEventListener('keydown',func)}
    for (let i = 0; i < text.length; i++) {
      if(blick[i] !== text.split(i,i++)){score -= 1}
    }
    
}
const block = window.addEventListener('keydown',func)

setInterval(() => {
  if (timer === 0) {
    clearInterval(interval)
    window.removeEventListener('keydown',func)                
  } else {
    timer--
    console.log(timer)
  }         
}, 1000)
</script>
 
<template>
<div>
    <div >
      {{ timer }}s
      <br>
      {{ score }}
    </div>
    <p>{{ text }}</p>
    <p>{{ blick }}</p>
</div>
</template>
 
<stlye scoped>

</stlye>