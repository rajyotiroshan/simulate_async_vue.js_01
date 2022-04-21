<template>
  <div class="btn_cont"><button @click="fetchData">Fetch Data</button></div>
  <table class="records" v-if="dataFetched">
    <thead class="records_head">
      <tr>
        <th>Name</th>
        <th>Roll No</th>
        <th>Total Marks(out of 500)</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="stud in studs" :key="stud.roll_no">
        <td>{{ stud.name }}</td>
        <td>{{ stud.roll_no }}</td>
        <td>{{ stud.marks }}</td>
      </tr>
    </tbody>
  </table>
  <div v-else-if="loading">Loading...</div>
  <div v-else>No data Available</div>
</template>

<script>
export default {
  data() {
    return {
      studs: [
        { name: "Rajan", roll_no: "12345", marks: "476" },
        { name: "Max", roll_no: "12334", marks: "489" },
        { name: "Ramanujan", roll_no: "10045", marks: "475" },
      ],
      dataFetched: true,
      loading: false,
    };
  },
  methods: {
    fetchData() {
      this.loading = true;
      let fetchedData = [];
      let that = this;
      setTimeout(() => {
        fetchedData = [
          { name: "Mohan", roll_no: "100045", marks: "496" },
          { name: "Clark", roll_no: "100034", marks: "493" },
          { name: "Ramanujan", roll_no: "100025", marks: "490" },
        ];
        if (fetchedData.legnth > 0) {
          that.dataFetched = true;
          that.loading = false;
        } else {
          that.dataFetched = false;
          that.loading = false;
        }
      }, 3000);
    },
  },
};
</script>

<style lang="less" scoped>
.records {
  margin: 0 auto;
  width: 50%;
  thead {
    width: inherit;
    tr {
      background-color: lightgrey;
      th {
        padding: 8px 5px;
      }
    }
  }
  tbody {
    width: 50%;
    tr {
      td {
        text-align: center;
        padding: 6px 4px;
      }
    }
  }
}
.btn_cont {
  text-align: center;
  button {
    padding: 5px 8px;
    background-color: lightgreen;
    color: white;
    font-weight: bold;
    font-size: 24px;
    font-family: "Courier New", Courier, monospace;
    border: none; //5px solid gray;
    border-radius: 5px;
    :hover {
      cursor: pointer;
    }
  }
}
</style>
