<template>
  <div>
    <!--BINARY TO STRING-->
    <div class="input-value__binary-to-string">
      <h1>Convert Binary to String:</h1>
      <input type="text" placeholder="Enter binary code..." v-model="binary" class="input-value">
      <div class="convert-button__container">
        <button class="convert-button" @click="getBinaryInputValue()">CONVERT</button>
      </div>
      <div class="input-value__content">{{ binResult.join('') }}</div>
      <button class="remove-value__button" @click="removeBinResult()">DELETE</button>
    </div>

    <!--STRING TO BINARY-->
    <div class="input-value__string-to-binary">
      <h1>Convert String to Binary:</h1>
      <input type="text" placeholder="Enter string..." v-model="string">
      <div class="convert-button__container">
        <button class="convert-button" @click="getStringInputValue()">CONVERT</button>
      </div>
      <div class="input-value__content">{{ stringBinResult.join() }}</div>
      <button class="remove-value__button" @click="removeStringResult()">DELETE</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Binary',
    data () {
      return {
        binary: '',
        binResult: [],
        string: '',
        stringResult: [],
        stringBinResult: [],
      }
    },
    methods: {
      getBinaryInputValue() {
        let inputValue = this.binary;
        let biString = inputValue.split(' ');
        let uniString = this.binResult;
        for (let i = 0; i < biString.length; i++) {
          uniString.push(String.fromCharCode(parseInt(biString[i], 2)));
        }
      },
      getStringInputValue() {
        let input = this.string;
        let output = this.stringResult;
        let binArr = this.stringBinResult;
        for (let i = 0; i < input.length; i++) {
          output += input[i].charCodeAt(0).toString(2) + " ";
        }
        binArr.push(output);
      },
      removeBinResult() {
        this.binResult = [];
      },
      removeStringResult() {
        this.stringBinResult = [];
      },
    }
  }
</script>

<style>

  /* CONVERT BINARY TO STRING */

  .input-value__binary-to-string {
    width: 100%;
    height: auto;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  input {
    outline: none;
    height: 32px;
    width: 640px;
    padding-left: 24px;
    overflow: hidden;
  }

  .input-value__content {
    height: 38px;
    width: 668px;
    font-size: 32px;
    background-color: #fff;
    border: 1px solid #A9A9A9;
    overflow: hidden;
  }

  .convert-button__container {
    padding: 48px 0;
  }

  .convert-button {
    height: 32px;
    width: 132px;
    border-radius: 28px;
    border: none;
    background-color: #1e90ff;
    color: #fff;
    outline: none;
    cursor: pointer;
    transition: 0.1s;
    position: relative;
  }

  .convert-button:hover {
    background-color: #32cd32;
  }

  .remove-value__button {
    height: 24px;
    width: 80px;
    border-radius: 28px;
    border: none;
    outline: none;
    color: #fff;
    background-color: #1e90ff;
    margin: 16px;
    cursor: pointer;
    font-size: 12px;
    transition: 0.1s;
  }

  .remove-value__button:hover {
    background-color: red;
  }

  /* CONVERT STRING TO BINARY */

  .input-value__string-to-binary {
    margin-top: 72px;
    padding-top: 50px;
    width: 100%;
    height: auto;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-top: 2px solid darkgrey;
  }

</style>
