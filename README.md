# Vue-JsBridge
JsBridge for Vue
  
`android 4.0+`  ,  `ios8.0+`  测试通过

## 引入  
main.js:  
```
import JsBridge from './你的路径/jsBridge'
Vue.use(JsBridge)
```
  
## 使用
component.vue:  
```
...
mounted() {
    this.JsBridge.registerHandler(
        'testJs',//注册的方法名，供原生调用
        (data, responseCallback) => {
        data = JSON.stringify(data)//收到原生发来的数据
        ...
        responseCallback("js say: got it!")//处理完成后返回给原生
    })
},
methods:{
    showToast(){
        this.JsBridge.callHandler(
            'toast',//原生声明的函数名称
            { data: `处理成功` },//发送给原生的数据
            (res) => {
                res = JSON.parse(res)//原生处理完成后返回的数据
                ...
            }
        )
    }
}
...
```
  
## 其他  
-  更多 `Obj-C` 与 `JavaScript` 交互请参阅  [WebViewJavascriptBridge](//github.com/marcuswestin/WebViewJavascriptBridge)  
-  真机调试可以使用 `android` 系统设备连接电脑打开 `chrome` 的 [chrome://inspect/#devices](chrome://inspect/#devices) 进行调试
