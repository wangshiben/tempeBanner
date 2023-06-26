<template>
  <div style="width: 100%">
    <div class="headerFirst"/>
<!--    下拉菜单相关 :span表示的是宽度-->
    <el-row style="height: 50px">
      <el-col :span="8">&nbsp;</el-col>
      <el-col :span="2" v-for="firstItem in pullsDownData" :key="firstItem.name" class="centerDisplay" style="margin-top: 20px">
        <template v-if="firstItem.data.length!==0">
        <el-dropdown >
          <span class="el-dropdown-link">
            {{firstItem.name}}<i class="el-icon-arrow-down el-icon--right"></i>
          </span>

        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item v-for="item in firstItem.data" :key="item">{{ item }}</el-dropdown-item>
        </el-dropdown-menu>

        </el-dropdown>
        </template>
        <template v-else>
          {{firstItem.name}}
        </template>
      </el-col>
    </el-row>
    <br><br>
<!--    下面是轮播图 -->
    <div class="banner centerDisplay">
      <div class="bannerContainer">
        <el-carousel >
          <el-carousel-item v-for="item in picUrl" :key="item">
            <img :src="item" style="max-width: 100%">
          </el-carousel-item>
        </el-carousel>
      </div>
    </div>

  </div>
</template>

<script>

export default {
  name: 'App',
  components: {},
  data() {
    return {
      pullsDownData:[
        {
          name:"首页",
          data:[]
        },
        {
          name: "医院概况",
          data:["医院简介", "职能部门", "科室导航", "历任领导"]
        },
        {
          name: "患者服务",
          data: ["预约挂号","门诊就医指南"]
        }
      ],
      picUrl:[
          "http://www.wchscu.cn/Uploads/Picture/2023/03/02/s6400876158bfd.png",
          "http://www.wchscu.cn/Uploads/Picture/2023/04/24/s64465e2d2a070.png",

      ]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.headerFirst {
  width: 100%;
  height: 50px;
  background: #6d1d29;
}
.banner{
  width: 100%;
}
.centerDisplay{
  display: flex;
  align-items: center;
  justify-items: center;
  flex-direction: column;
}
.bannerContainer{
  width: 80%;
}
</style>
