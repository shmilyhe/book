# UAS管理接口

[TOC]
## 组织机构

### 根据ID找机构
url: /uas/manager/findOrgById
method:get
例：https://wx.datastars.net/uas/manager/findOrgById?id=8396806fe26f41f188ed161cb64c614d
返回值：
```
{"code" : 0,
"data" : 
{"name" : "公司总部","id" : "8396806fe26f41f188ed161cb64c614d","level" : 0,"code" : "root","mask" : "root"}
}
```

### 根据ID找机构
url: /uas/manager/findSubOrg
method:get
例：https://wx.datastars.net/uas/manager/findSubOrg?id=8396806fe26f41f188ed161cb64c614d
返回值：
```
{"code" : 0,
"data" : 
{"name" : "公司总部","id" : "8396806fe26f41f188ed161cb64c614d","level" : 0,"code" : "root","mask" : "root"}
}
```


### 根据掩码找下属机构
url: /uas/manager/findSubOrg
method:get
例：https://wx.datastars.net/uas/manager/findSubOrg?mask=root
返回值：
```
{"code" : 0,"data" : [{"name" : "某某公司","id" : "8396806fe26f41f188ed161cb64c614d","level" : 0,"code" : "root","mask" : "root"},{"name" : "综合管理部","id" : "0b2e4fe58a9644e982adcd9d64d9f244","level" : 0,"pid" : "8396806fe26f41f188ed161cb64c614d","code" : "universual","mask" : "root:universual"},{"name" : "总经办","id" : "2feabcf1f74c459daf617792224ca56b","level" : 0,"pid" : "8396806fe26f41f188ed161cb64c614d","code" : "ceooffice","mask" : "root:ceooffice"},{"name" : "市场部","id" : "d0054943a02c48958f85a712c6d3b351","level" : 0,"pid" : "8396806fe26f41f188ed161cb64c614d","code" : "marketting","mask" : "root:marketting"}]
}
```

### 根据ID找下一级机构
url: /uas/manager/childrenOrg
method:get
例：https://wx.datastars.net/uas/manager/childrenOrg?id=8396806fe26f41f188ed161cb64c614d
返回值：
```
{"code" : 0,"data" : [{"name" : "综合管理部","id" : "0b2e4fe58a9644e982adcd9d64d9f244","level" : 0,"pid" : "8396806fe26f41f188ed161cb64c614d","code" : "universual","mask" : "root:universual"},{"name" : "总经办","id" : "2feabcf1f74c459daf617792224ca56b","level" : 0,"pid" : "8396806fe26f41f188ed161cb64c614d","code" : "ceooffice","mask" : "root:ceooffice"},{"name" : "市场部","id" : "d0054943a02c48958f85a712c6d3b351","level" : 0,"pid" : "8396806fe26f41f188ed161cb64c614d","code" : "marketting","mask" : "root:marketting"}]}
```

### 移动机构到另一个机构下面
url: /uas/manager/appendToOrg
参数 
pid:父ID
id:机构ID
method:get
例：https://wx.datastars.net/uas/manager/appendToOrg?pid=8396806fe26f41f188ed161cb64c614d&id=0b2e4fe58a9644e982adcd9d64d9f244
返回值：
```
{"code" : 0,"data" :"true"}
```
### 新增机构
url: /uas/manager/addOrg
参数 
name:名称
pid:父机构ID
code:

method:post
例：https://wx.datastars.net/uas/manager/addOrg
请求主体
```
{"name" : "公司总部","level" : 0,"code" : "root","mask" : "root",pid:"1231"}
```
返回值：
```
{"code" : 0,"data" :
{"name" : "公司总部","id" : "8396806fe26f41f188ed161cb64c614d","level" : 0,"code" : "root","mask" : "root","pid":"123"}
}
```


### 删除机构
url: /uas/manager/delOrg
参数 
id:名称

method:get
例：https://wx.datastars.net/uas/manager/delOrg?id=8396806fe26f41f188ed161cb64c614d

返回值：
```
{"code" : 0,"data" :"true"}
```

### 更新机构
url: /uas/manager/updateOrg
参数 
name:名称
pid:父机构ID
code:

method:post
例：https://wx.datastars.net/uas/manager/updateOrg
请求主体
```
{"id":"8396806fe26f41f188ed161cb64c614d",name" : "公司总部","level" : 0,"code" : "root","mask" : "root",pid:"1231"}
```
返回值：
```
{"code" : 0,"data" :
{"name" : "公司总部","id" : "8396806fe26f41f188ed161cb64c614d","level" : 0,"code" : "root","mask" : "root","pid":"123"}
}
```

### 查询机构
url: /uas/manager/listOrg
参数 
name:名称
page:父机构ID
pageSize:
mask:
all:是否查全部
method:post/get
例：https://wx.datastars.net/uas/manager/listOrg

返回值：
```
{"code" : 0,"data" :
[{"name" : "公司总部","id" : "8396806fe26f41f188ed161cb64c614d","level" : 0,"code" : "root","mask" : "root","pid":"123"},...]，
"page" : {"totalPage" : 1,"page" : 1,"rows" : 4,"pageSize" : 10}
}
```

## 资源管理

### 新增资源
url: /uas/manager/addAccess
参数 
name:名称
pid:父ID
code:
url:访问URL
app:应用名称
pathMask：
mode:模式 2、可匿名访问的 

method:post
例：https://wx.datastars.net/uas/manager/addAccess
请求主体
```
{"name" : "静态资源","type" : "url","level" : 0,"code" : "static","url" : "/static/**","app" : "default","pathMask" : "","mode" : 2}
```
返回值：
```
{"code" : 0,"data" : {"name" : "静态资源","id" : "0","type" : "url","level" : 0,"code" : "static","url" : "/static/**","app" : "default","pathMask" : "","mode" : 2}}
```

### 按ID查找资源
url: /uas/manager/findAccessById
参数 
name:名称
pid:父ID
code:
url:访问URL
app:应用名称
pathMask：
mode:模式 2、可匿名访问的 

method:get
例：https://wx.datastars.net/uas/manager/findAccessById?id=0

返回值：
```
{"code" : 0,"data" : {"name" : "静态资源","id" : "0","type" : "url","level" : 0,"code" : "static","url" : "/static/**","app" : "default","pathMask" : "","mode" : 2}}
```

### 更新资源
url: /uas/manager/updateAccess
参数 
name:名称
pid:父ID
code:
url:访问URL
app:应用名称
pathMask：
mode:模式 2、可匿名访问的 

method:post
例：https://wx.datastars.net/uas/manager/updateAccess
请求主体
```
{"code" : 0,"data" : {"name" : "静态资源","id" : "0","type" : "url","level" : 0,"code" : "static","url" : "/static/**","app" : "default","pathMask" : "","mode" : 2}}
```
返回值：
```
{"code" : 0,"data" : {"name" : "静态资源","id" : "0","type" : "url","level" : 0,"code" : "static","url" : "/static/**","app" : "default","pathMask" : "","mode" : 2}}
```


### 查询所有资源
url: /uas/manager/findAllAccess
参数 
app:应用

method:post/get
例：https://wx.datastars.net/uas/manager/findAllAccess?app=default

返回值：
```
{"code" : 0,"data" : [{"name" : "静态资源","id" : "0","type" : "url","level" : 0,"code" : "static","url" : "/static/**","app" : "default","pathMask" : "","mode" : 2},{"name" : "主页","id" : "4","type" : "url","level" : 0,"code" : "static","url" : "/css/**","app" : "default","pathMask" : "","mode" : 2},{"name" : "主页","id" : "5","type" : "url","level" : 0,"code" : "static","url" : "/js/**","app" : "default","pathMask" : "","mode" : 2},{"name" : "主页","id" : "7","type" : "url","level" : 0,"code" : "static","url" : "/lib/**","app" : "default","pathMask" : "","mode" : 2},{"name" : "主页","id" : "8","type" : "url","level" : 0,"code" : "static","url" : "/images/**","app" : "default","pathMask" : "","mode" : 2},{"name" : "管理模块","id" : "1","type" : "menu","level" : 0,"code" : "static","url" : "/admin/**","app" : "default","pathMask" : "01","mode" : 0},{"name" : "订单模块","id" : "2","type" : "menu","level" : 0,"code" : "static","url" : "/order/**","app" : "default","pathMask" : "02","mode" : 0},{"name" : "门户模块","id" : "3","type" : "url","level" : 0,"code" : "menu","url" : "/","app" : "default","pathMask" : "03","mode" : 3},{"name" : "门户模块","id" : "6","type" : "url","level" : 0,"code" : "menu","url" : "/index","app" : "default","pathMask" : "03","mode" : 3}]}
```

### 按掩码查询资源
url: /uas/manager/findAccessByMask
参数 
app:应用
mask:掩码
method:get
例：https://wx.datastars.net/uas/manager/findAccessByMask?app=default&mask=root

返回值：
```
{"code" : 0,"data" : [{"name" : "静态资源","id" : "0","type" : "url","level" : 0,"code" : "static","url" : "/static/**","app" : "default","pathMask" : "","mode" : 2},{"name" : "主页","id" : "4","type" : "url","level" : 0,"code" : "static","url" : "/css/**","app" : "default","pathMask" : "","mode" : 2},{"name" : "主页","id" : "5","type" : "url","level" : 0,"code" : "static","url" : "/js/**","app" : "default","pathMask" : "","mode" : 2},{"name" : "主页","id" : "7","type" : "url","level" : 0,"code" : "static","url" : "/lib/**","app" : "default","pathMask" : "","mode" : 2},{"name" : "主页","id" : "8","type" : "url","level" : 0,"code" : "static","url" : "/images/**","app" : "default","pathMask" : "","mode" : 2},{"name" : "管理模块","id" : "1","type" : "menu","level" : 0,"code" : "static","url" : "/admin/**","app" : "default","pathMask" : "01","mode" : 0},{"name" : "订单模块","id" : "2","type" : "menu","level" : 0,"code" : "static","url" : "/order/**","app" : "default","pathMask" : "02","mode" : 0},{"name" : "门户模块","id" : "3","type" : "url","level" : 0,"code" : "menu","url" : "/","app" : "default","pathMask" : "03","mode" : 3},{"name" : "门户模块","id" : "6","type" : "url","level" : 0,"code" : "menu","url" : "/index","app" : "default","pathMask" : "03","mode" : 3}]}
```

### 移动资源到另一下资源下
url: /uas/manager/appendToAccess
参数 
id:id
pid:父id
method:get
例：https://wx.datastars.net/uas/manager/appendToAccess?id=03&pid=01

返回值：
```
{"code" : 0,"data" :"true"}
```
### 删除资源
url: /uas/manager/delAccess
参数 
id:id

method:get
例：https://wx.datastars.net/uas/manager/delAccess?id=8396806fe26f41f188ed161cb64c614d

返回值：
```
{"code" : 0,"data" :"true"}
```

## 角色管理



### 查询所有资源
url: /uas/manager/listAllRoles
参数 
app:应用

method:post/get
例：https://wx.datastars.net/uas/manager/listAllRoles?app=default

返回值：
```
{"code" : 0,"data" : [{"name" : "管理员","id" : "0","code" : "admin","app" : "default"},{"name" : "普通用户","id" : "1","code" : "normal","app" : "default"},{"name" : "禁止用户","id" : "2","code" : "deny","app" : "default"}]}
```

### 新增资源
url: /uas/manager/addRole
参数 
name:名称
code:code
app:应用名称


method:post
例：https://wx.datastars.net/uas/manager/addRole
请求主体
```
{"name" : "管理员","code" : "admin","app" : "default"}
```
返回值：
```
{"code" : 0,"data" : {"name" : "管理员","id" : "0","code" : "admin","app" : "default"}}
```

### 更新资源
url: /uas/manager/updateRole
参数 
name:名称
code:code
app:应用名称


method:post
例：https://wx.datastars.net/uas/manager/addRole
请求主体
```
{"name" : "管理员","id": "01","code" : "admin","app" : "default"}
```
返回值：
```
{"code" : 0,"data" : {"name" : "管理员","id" : "0","code" : "admin","app" : "default"}}
```

### 删除角色
url: /uas/manager/delRole
参数 
id:名称

method:get
例：https://wx.datastars.net/uas/manager/delRole?id=8396806fe26f41f188ed161cb64c614d

返回值：
```
{"code" : 0,"data" :"true"}
```

### 角色添加用户
url: /uas/manager/grantUserRole
参数 
rid:角色ID
uid:用户ID
method:get
例：https://wx.datastars.net/uas/manager/grantUserRole?uid=8396806fe26f41f188ed161cb64c614d&rid=xxxxx

返回值：
```
{"code" : 0,"data" :"true"}
```

### 角色添加资源
url: /uas/manager/accessToRole
参数 
rid:角色ID
aid:资源ID
method:get
例：https://wx.datastars.net/uas/manager/accessToRole?uid=8396806fe26f41f188ed161cb64c614d&rid=xxxxx

返回值：
```
{"code" : 0,"data" :"true"}
```
## 用户管理

### 新增用户
url:/uas/manager/addUser
参数：
id :id
name :姓名
account :账号
title :职称
cellphone :手机
mail :邮箱
orgid :机构id,
gender :性别
avatar :头像
src :来源
deptId:"二级部门"
posistion:岗位
level:0
area:区域
status 1
输入参数：
```
{	name :"test",
	account :"test",
	title :"test",
	cellphone :"test",
	mail :"test",
	orgid :"test",
	gender :"test",
	avatar :"test",
	src :"test",
	posistion:"0",
	level:0,
	area:0，
	status: 1}
```

输出参数：
```
{"code" : 0,"data" :
	{id :"12312312312312312",
	name :"test",
	account :"test",
	title :"test",
	cellphone :"test",
	mail :"test",
	orgid :"test",
	gender :"test",
	avatar :"test",
	src :"test",
	deptId:"二级部门ID",
	posistion:"0",
	level:0,
	area:0，
	status :1}
}
```
### 更新用户
url:/uas/manager/updateUser
参数：
id :id
name :姓名
account :账号
title :职称
cellphone :手机
mail :邮箱
orgid :机构id,
gender :性别
avatar :头像
src :来源
deptId:"二级部门"
level:0
area:区域
posistion:岗位
status 1
输入参数：
```
{
	id :"12312312312312312",
	name :"test",
	account :"test",
	title :"test",
	cellphone :"test",
	mail :"test",
	orgid :"test",
	gender :"test",
	avatar :"test",
	src :"test",
	posistion:"0",
	level:0,
	area:0，
	status :1}
```

输出参数：
```
{"code" : 0,"data" :
	{id :"12312312312312312",
	name :"test",
	account :"test",
	title :"test",
	cellphone :"test",
	mail :"test",
	orgid :"test",
	gender :"test",
	avatar :"test",
	src :"test",
	deptId:"二级部门ID",
	level:0,
	area:0，
	status:1}
}
```



### 按ID查找用户
url: /uas/manager/findUserById
参数 
id:ID
method:get
例：https://wx.datastars.net/uas/manager/findUserById?id=8396806fe26f41f188ed161cb64c614d&rid=xxxxx

返回值：
```
{"code" : 0,"data" :
	{id :"12312312312312312",
	name :"test",
	account :"test",
	title :"test",
	cellphone :"test",
	mail :"test",
	orgid :"test",
	gender :"test",
	avatar :"test",
	src :"test",
	dept2:"二级部门ID",
	dept3:"二级部门ID",
	posistion:"0",
	level:0,
	area:0，
	status :1}
}
```


### 查找用户
url: /uas/manager/findUser
参数 
orgid:机构
orgmask:机构掩码
name:姓名或账号
posistion:岗位
page:页码
pageSize:每页显示条数

method:get
例：https://wx.datastars.net/uas/manager/findUser?orgid=8396806fe26f41f188ed161cb64c614d&rid=xxxxx

返回值：
```
{"code" : 0,"data" :[
	{id :"12312312312312312",
	name :"test",
	account :"test",
	title :"test",
	cellphone :"test",
	mail :"test",
	orgid :"test",
	gender :"test",
	avatar :"test",
	src :"test",
	dept2:"二级部门ID",
	dept3:"三级部门ID",
	posistion:"0",
	level:0,
	area:0，
	status :1}],
	"page" : {"totalPage" : 1,"page" : 1,"rows" : 4,"pageSize" : 10}
}
```

### 删除用户
url: /uas/manager/delUser
参数 
id:id

method:get
例：https://wx.datastars.net/uas/manager/delUser?id=8396806fe26f41f188ed161cb64c614d

返回值：
```
{"code" : 0,"data" :"true"}
```

### 修改用户状态
url: /uas/manager/userStatus
参数 
id:id
status：状态[0-3] 0:注册 ，1，正常 2、离职

method:get
例：https://wx.datastars.net/uas/manager/userStatus?id=8396806fe26f41f188ed161cb64c614d&status=1

返回值：
```
{"code" : 0,"data" :"true"}
```

### 修改用户密码
url: /uas/manager/changePwd
参数 
id:id
pwd：密码 ,不填密码由系统随机产生6位密码
method:get
例：https://wx.datastars.net/uas/manager/changePwd?id=8396806fe26f41f188ed161cb64c614d&pwd=123456

返回值：
```
{"code" : 0,"data" :"123456"}
```


### 按角色查找用户
url: /uas/manager/findUserByRole
参数 
rid:角色ID
name：姓名或账号
page:页码
pageSize:每页显示多少
method:get
例：https://wx.datastars.net/uas/manager/findUserByRole?id=8396806fe26f41f188ed161cb64c614d&name=123456

返回值：
```
{"data" : [{"name" : "张无忌","id" : "0","account" : "admin","title" : "管理员"},
{"name" : "杨过","id" : "1","account" : "admin1","title" : "管理员"},
{"name" : "张三","id" : "2",,"account" : "guest","title" : "攻城师"},
{"name" : "谢迅","id" : "3","account" : "guest2","title" : "攻城师"}],"page" : {"totalPage" : 1,"page" : 1,"rows" : 4,"pageSize" : 10}}
```



## 岗位管理

### 新增岗位
url: /uas/manager/addPosition
参数 
name：姓名
code:code

method:post
例：https://wx.datastars.net/uas/manager/addPosition
输入值：
```
{name:"java研发",code:"dev_java"}
```
返回值：
```
{"data" :{id:"123123123123213",name:"java研发",code:"dev_java"}}
```

### 更新岗位
url: /uas/manager/updatePosition
参数 
id:id
name：姓名
code:code

method:post
例：https://wx.datastars.net/uas/manager/updatePosition
输入值：
```
{id:"123123123123213",name:"java研发",code:"dev_java"}
```
返回值：
```
{"data" :{id:"123123123123213",name:"java研发",code:"dev_java"}}
```

### 删除岗位
url: /uas/manager/delPosition
参数 
id:id


method:get
例：https://wx.datastars.net/uas/manager/delPosition?id=12312313

返回值：
```
{"data" :"true"}
```

### 查询所有岗位
url: /uas/manager/listPosition
参数 


method:get
例：https://wx.datastars.net/uas/manager/listPosition

返回值：
```
{"data" :[{id:"123123123123213",name:"java研发",code:"dev_java"}]}
```









