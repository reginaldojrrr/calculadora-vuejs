<script setup>
import { reactive } from 'vue';

const operacao = reactive({
    valorA: '',
    valorB: '',
    operador: '+',
    resultado: 0
})

function calcular() {
    const valorA = parseInt(operacao.valorA);
    const valorB = parseInt(operacao.valorB);

    if (operacao.operador === '+') {
        operacao.resultado = valorA + valorB;
    } else if (operacao.operador === '-') {
        operacao.resultado = valorA - valorB;
    } else if (operacao.operador === 'x') {
        operacao.resultado = valorA * valorB;
    } else if (operacao.operador === '÷') {
        operacao.resultado = valorA / valorB;
    } else if (operacao.operador === '%') {
        operacao.resultado = (valorA / 100) * valorB;
    } 
}

</script>

<template>
    <div class="row">
        <div class="col-2">
            <input @input="calcular()" v-model="operacao.valorA" class="form-control" type="number" id="inputA" placeholder="0">
        </div>
        <div class="col-2">
            <select @change="calcular()" v-model="operacao.operador" class="form-select" id="operation">
                <option value="+">+</option>
                <option value="-">-</option>
                <option value="x">x</option>
                <option value="÷">÷</option>
                <option value="%">%</option>
            </select>
        </div>
        <div class="col-2">
            <input @input="calcular()" v-model="operacao.valorB" class="form-control" type="number" id="inputB" placeholder="0">
        </div>
    </div>
    <div class="row">
        <div class="col-12">
            <h3 v-if="operacao.valorA.length !== 0 && operacao.valorB.length !== 0">O resultado é:</h3>
            <h3 v-else="operacao.valorA.length == 0 && operacao.valorB.length == 0">Digite um número...</h3>
        </div>
    </div>
    <div class="row">
        <h1 v-if="operacao.valorA.length !== 0 && operacao.valorB.length !== 0">{{ operacao.resultado }}</h1>
    </div>
</template>

<style scoped>
.row {
    display: flex;
    justify-content: center;
    text-align: center;
    margin: 40px 0;
}

input::placeholder {
    color: #adababcc;
}

h1, h3 {
    margin: 0;
}

</style>