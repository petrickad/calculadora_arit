<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    num1: '',
    num2: '',
    operation: '',
    resultado: '',
  });

  const calcular = () => {
    const a = parseFloat(estado.num1);
    const b = parseFloat(estado.num2);
    
    switch (estado.operation) {
      case 'adicao':
        estado.resultado = a + b;
        break;
      case 'subtracao':
        estado.resultado = a - b;
        break;
      case 'multiplicacao':
        estado.resultado = a * b;
        break;
      case 'divisao':
        if (b !== 0) {
          estado.resultado = a / b;
        } else {
          estado.resultado = 'Erro: Divisão por zero';
        }
        break;
      default:
        estado.resultado = 'Operação inválida';
    }
  }

  console.log(estado);
</script>

<template>
  <div class="container">
    <header>
      <h1>Calculadora Aritmética</h1>
    </header>
    <p>Escolha a operação</p>
    <select v-model="estado.operation" @change="calcular" class="form-control w-50 text-center mb-4">
      <option value="adicao">Adição (+)</option>
      <option value="subtracao">Subtração (-)</option>
      <option value="multiplicacao">Multiplicação (x)</option>
      <option value="divisao">Divisão (/)</option>
    </select>
    <input v-model="estado.num1" @input="calcular" class="form-control w-50 mb-2 text-center" type="number" placeholder="Digite o primeiro número">
    <input v-model="estado.num2" @input="calcular" class="form-control w-50 text-center" type="number" placeholder="Digite o segundo número">
    <p v-if="estado.resultado !== ''" class="mt-3">Resultado: {{ estado.resultado }}</p>
  </div>
</template>

<style scoped>
  .container {
    border-radius: 12px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 90vh;
    background-color: #7c7a7aa6;
  }

  h1 {
    font-size: 2rem;
    color: #333;
  }

</style>
