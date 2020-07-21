# 接口

POST 都是 JSON + UTF-8 格式。

## 通用返回规则

```json
{
    "code":0,
    "message":"ok",
    "data":{
        "id":1111
    }
}
```

## 通用 code

- 0：正常
- 1：不正确的用户名或密码
- 2：验证码错误
- 3：用户名重复 
- 4：邮箱重复
- 5：没有权限
- 6：系统错误
- 7：其他错误

## 登录、注册

### 登录

方式：POST

path：/auth/login

参数：

- 用户名(String)
- 密码(String)
- 验证码(String)

返回：

- Token(String)：JWT


### 注册

方式：POST

path：/auth/signup

参数：

- 用户名(String)
- 密码(String)
- 邮箱(String)
- 验证码(String)


<!-- 
## 用户管理接口

### 绑定 GitHub

Auth2 


### 解除绑定 GitHub
 -->

## 题目接口

### 获取题目

无需 Token

方式：GET

path：/exercise/<id>

返回：

```json

{
    "id":1000,
    "title":"",
    "data":"",
    "max_time":0,
    "max_cpu":0.0,
    "max_memory":0,
    "author":"",
    "create_time":1000000,
    "pass_rate":80.0,
    "need_env":[
        {
            "step":0,
            "name":"BASE_DIR",
            "intro":"根目录",
            "type":"path"
        }
    ]
}
```

### 提交题目

后端记得修改目录分隔符

方式：POST

path：/exercise/<id>

请求：

```json
{
    "id":1000,
    "file_name":"1111",
    "need_env":[
        {
            "name":"BASE_DIR",
            "value":"/"
        }
    ]
}
```
返回

- 提交ID

### 获取所有题目

无需 Token

方式：GET

path：/exercise

参数：begin：开始的位置，size：请求的数量

[
    {

    }
]

### 新增题目

方式：PUT

path：/exercise

请求
```JSON
{
    "title":"",
    "data":"",
    "max_time":0,
    "max_cpu":0.0,
    "max_memory":0,
    "need_env":[
        {
            "step":0,
            "name":"BASE_DIR",
            "intro":"根目录"
        }
    ]
}
```


## 评测结果

方式：GET

path：/result/<id>

回复：
```JSON
{
    "stats":"pass",
    "message":"通过"
}
```


## 杂项


### 文件上传请求

请求:POST

path：/upload


参数：

- 文件 hash
- 文件名字
- 文件大小


返回：

- 上传路径
- 文件 ID