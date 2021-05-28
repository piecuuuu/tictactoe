<template>
  <div class="game">
    <div class="board">
      <div class="cell" @click="cellClick(0, 0)">{{ board[0][0] }}</div>
      <div class="cell" @click="cellClick(0, 1)">{{ board[0][1] }}</div>
      <div class="cell" @click="cellClick(0, 2)">{{ board[0][2] }}</div>
      <div class="cell" @click="cellClick(1, 0)">{{ board[1][0] }}</div>
      <div class="cell" @click="cellClick(1, 1)">{{ board[1][1] }}</div>
      <div class="cell" @click="cellClick(1, 2)">{{ board[1][2] }}</div>
      <div class="cell" @click="cellClick(2, 0)">{{ board[2][0] }}</div>
      <div class="cell" @click="cellClick(2, 1)">{{ board[2][1] }}</div>
      <div class="cell" @click="cellClick(2, 2)">{{ board[2][2] }}</div>
      <button v-on:click="reset">Reset Game</button>
    </div>
    <div class="result"></div>
    <!-- <div class="turn">{{ round }}</div> -->
  </div>
</template>

<script>
export default {
  // props: {
  //   value: String,
  // },
  data() {
    return {
      board: [
        ['', '', ''],
        ['', '', ''],
        ['', '', ''],
      ],
      players: ['X', 'O'],
      round: 1,
      winCombo: [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 4, 8],
    [2, 4, 6],
    [1, 4, 7],
    [0, 3, 6],
    [2, 5, 8],
  ],
    };
  },
  watch: {
    
  },
  methods: {
    logicGame() {
      for (let i=0; i<=this.winCombo.length; i++) {
        for (let j=0; j<=this.board.length; j++) {
         if (this.winCombo[i] == this.board[j]) {
           alert('hakunamatata');
           console.log(this.winCombo);
           console.log(this.board);
         }
        }
      }
    },
    cellClick(col, row) {
      if (this.board[col][row] !== '') {
         return this.cellClick;
      }
      this.turn = this.round % 2 === 0 ? this.players[1] : this.players[0];
      this.board[col][row] = this.turn;
      // event.target.value.add(this.turn);
      this.round++;
      this.logicGame();
    },
    resetGame() {

    }
  }
};
</script>

<style>
  .cell {
    width: 64px;
    height: 64px;
    border: 2px solid rgb(75,75,75);
    font-size: 42px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }

  .cell:hover {
    background: rgb(150, 150, 150);
  }
    .board {
    /* background-color: bisque; */
    display: flex;
    flex-wrap: wrap;
    width: 204px;
    height: 204px;
  }

</style>



