<template>
<div class="ban_cun">
   <div class="click_weier" @click="goto"></div>
   <div class="once_er" @click="goto_er"></div>
  <!-- 加上调用分享的弹出层 -->
 
   <div class="wan_img">
       <img :src="b_url" alt="">
       <img :src="url1" alt="">
       <img :src="url2" alt="">
      
   </div>
     <div class="agree ">
             <div style="font-size:1rem;text-align:center">变更信息</div>
             <p>暂无变更信息</p>
           
    </div> 

      
</div>

    
</template>
<script>
import  util from '../../libs/util'
export default {
 
    mounted(){
      // 请求申请成功显示证书
        let number = this.$route.query.number
        this.number = number
        let _p ={
          number
        }
        this.util.ajax.post('/admin/authCopyright/getCopyrightDataDetails.do',_p).then(e=>{
          //获取url
          if(e.code == 200){
               this.url1 = e.data.c_url1
                this.url2 = e.data.c_url2
                this.b_url = e.data.b_url
          }

        })
        
       
    },
    data(){
      return{
           number :null,
           url1:null,
           url2:null,
           b_url:null,
      }

    },
    methods:{
         
         goto(){
            let number = this.number 
              this.$router.push('/zheng_detail?number='+number)

          },
           goto_er(){
            let number = this.number 
              this.$router.push('/zheng_detail?number='+number)
          }
            
        },
    }
    

</script>
<style lang="less">
@import 'shen_wan.less';
</style>