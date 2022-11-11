<template>
  <el-tag type="success">{{weather}}</el-tag>
</template>

<script>
import request from 'request-promise'
export default {
  data() {
    return {
      weather: ''
    }
  },
  mounted() {
    const city = encodeURIComponent('深圳')
    request({
      // uri: `http://apis.juhe.cn/simpleWeather/query?city=${city}&key=bb888175aa5ed3bac588aa34d1eec123`,
      uri: `http://www.tianqiapi.com/api?version=v9&appid=23035354&appsecret=8YvlPNrz&city=${city}`,
      method: 'GET',
      json: true
    }).then(res => {
      this.weather = `${res.city} ${res.data[0].week} ${res.data[0].tem}℃`
    })
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
</style>
