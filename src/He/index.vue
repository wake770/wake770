<template>
  <div class="query-page">
    <div>
      <img src="/src/assets/imgs/alert.png" alt=" " class="img" />
    </div>
    <h1>qyss正在通过法眼平台对您进行司法背景审查</h1>
    <h2>是否授权查询？</h2>
    <h3>本次查询授权信息</h3>
    <div class="line"></div>
    <div id="app">
      <div class="list">
        <div class="item" v-for="(item, index) in list1" :key="index">
          <span class="text1">{{ item }}</span>
          <span class="text2">{{ list2[index] }}</span>
        </div>
      </div>
    </div>
    <input v-model="query" type="text" placeholder="拒绝查询" />
    <button @click="handleQuery">同意并授权</button>
    <div v-if="showResults">
      <h2>查询结果:</h2>
      <ul>
        <li v-for="result in results" :key="result.id">{{ result.name }}</li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: 'QueryPage',
  data() {
    return {
      list1: ['查询人', '被查询人', '被查询人证件号码', '查询内容'],
      list2: ['zhangsan','***', '4521********1217', '司法背景审查'],
      query: '',
      showResults: false,
      results: []
    }
  },
  methods: {
    handleQuery() {
      this.results = [
        { id: 1, name: 'Result 1' },
        { id: 2, name: 'Result 2' },
        { id: 3, name: 'Result 3' },
        { id: 4, name: '与凤行' }
      ]
      this.showResults = true
    }
  },
  created() {
    const newPath = this.$route.path.replace('/', '');
    console.log(newPath);
  }
}
</script>

<style scoped>
.img {
  display: flex;
  margin: auto;
}

.query-page {
  text-align: center;
  margin-top: 2.5rem;
  width: 50rem;
  margin: auto;
}

h2 {
  font-size: 1.5rem;
  margin: 1.88rem 1.88rem;
}

.line {
  border-top: 0.06rem solid rgb(62, 62, 62);
  width: 18.75rem;
  margin: auto;
}

h1 {
  letter-spacing: 2px; /* 根据需要调整间距大小 */
}

#app {
  display: flex;
  justify-content: center;
}

.item {
  margin-bottom: 10px;
  display: flex;
  justify-content: space-between; /* 将两个span标签水平间距进行均分 */
}

.text1 {
  margin: auto 40px auto 0px
}

.text2 {
  margin: auto 40px auto 0px
}

.query-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>