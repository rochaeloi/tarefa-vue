<script setup>
import { reactive, computed } from 'vue'

const state = reactive({
  numero1: 0,
  numero2: 0,
  operacao: 'soma'
})

const resultado = computed(() => {
  let res = 0;
  switch (state.operacao) {
    case 'soma':
      res = state.numero1 + state.numero2;
      break;
    case 'subtracao':
      res = state.numero1 - state.numero2;
      break;
    case 'multiplicacao':
      res = state.numero1 * state.numero2;
      break;
    case 'divisao':
      res = state.numero2 !== 0 ? state.numero1 / state.numero2 : 'Erro: Divisão por zero';
      break;
  }
  return res;
});
</script>

<template>
  <div class="container" id="app">
    <h1 class="text-center mt-5">Calculadora Aritmética</h1>
    <div class="calculator row justify-content-center mt-4">
      <div class="col-md-4">
        <input class="form-control mb-3" type="number" v-model.number="state.numero1" placeholder="Insira o primeiro número" />
      </div>
      <div class="col-md-2">
        <select class="form-control mb-3" v-model="state.operacao">
        <option value="soma">+</option>
        <option value="subtracao">-</option>
        <option value="multiplicacao">*</option>
        <option value="divisao">/</option>
      </select>
      </div>
      <div class="col-md-4">
        <input class="form-control mb-3" type="number" v-model.number="state.numero2" placeholder="Insira o segundo número" />
      </div>
      <div class="resultado text-center">
        <p class="h3">
          Resultado:<span class="font-weight-bold">{{ resultado }}</span>
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped>
#app {
  text-align: center;
  margin-top: 50px;
}

input, select {
  margin: 10px;
  padding: 10px;
  font-size: 1.2em;
}

.resultado {
  margin-top: 20px;
  font-size: 1.5em;
  font-weight: bold;
}
</style>