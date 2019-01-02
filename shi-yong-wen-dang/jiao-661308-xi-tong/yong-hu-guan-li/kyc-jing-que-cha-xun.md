#### 1.根据用户 id / email / mobile 进行精确查询

```
GET    

A: http://localhost:8080/user/kyc/search?[condition={condition}][&startDate={startDate}&endDate={endDate}]&page={page}&size={size}&sort=[sort]
B: http://localhost:8080/user/kyc/search?[type={type}][&userId={userId}][&email={email}][&moobile={mobile}][&startDate={startDate}&endDate={endDate}]&page={page}&size={size}&sort=[sort]
```

* **接口说明：**

  * **注意 \[ \] 内的内容，为可选项**
  * **时间非必传参数**
  * **A、B可以直接使用时间查询**

* **参数说明：选填任意一个，不支持多选**

  * A 查询：
    * String** condition : **
      * **如果查询 KYC 认证级别，则输入对应级别查询（normal、C1、C2、C3、aLiYunOcr2 等自定义级别）**
      * **如果查询 KYC 认证状态，则输入 PASSED、PENDING、REJECTED**
    * Long **startDate : 1541753926（毫秒时间戳）**
    * Long **endDate : 1541821711000（毫秒时间戳）**
    * 分页参考其他接口用法
  * B 查询：
    * String **type : user（用户创建时间）、kyc（认证时间）两种类型。**
    * Long **userId : 不允许模糊查询**
    * String **email : 允许模糊查询**
    * String **mobile : 允许模糊查询**
    * Long **startDate : 1541753926（毫秒时间戳）**
    * Long **endDate : 1541821711000（毫秒时间戳）**
    * 分页参考其他接口用法

* **返回结果：**

```
{
  "content": [
    {
      "id": 5,
      "email": "32694110@qq.com",
      "mobile": "+86-17610016050",
      "createdDate": "2018-09-08T15:53:01Z",
      "level": "normal",
      "status": "PASSED",
      "data": null,
      "extraData": null,
      "description": null,
      "extension": null,
      "kycCreatedDate": "2018-11-09T03:48:31Z",
      "kycLastModifiedDate": "2018-11-09T18:49:11Z",
      "authorityName": [
        "ROLE_ADMIN,ROLE_USER"
      ]
    },
    ......[other data]
  ],
  "size": 20,
  "totalElements": 1,
  "pageable": {
    "sort": {
      "sorted": false,
      "unsorted": true
    },
    "offset": 0,
    "pageSize": 20,
    "pageNumber": 0,
    "unpaged": false,
    "paged": true
  },
  "last": true,
  "totalPages": 1,
  "sort": {
    "sorted": false,
    "unsorted": true
  },
  "first": true,
  "numberOfElements": 1,
  "number": 0
}
```

* **异常情况：无**

#### 2.查询KYC 用户详细信息

```
GET    http://localhost:8080/user/kyc/details/{userId}
```

* **接口使用说明：**

* **参数说明：**

  * Long ** userId **

* **返回结果：**

```
{
  "id": 5,
  "email": "32694110@qq.com",
  "mobile": "+86-17610016050",
  "createdDate": "2018-09-08T15:53:01Z",
  "level": "normal",
  "status": "PASSED",
  "data": "{\"fullName\":{\"type\":\"text\",\"data\":\"龚涛\"},\"birthday\":{\"type\":\"select\",\"data\":\"2017-2-2\"},\"country\":{\"type\":\"text\",\"data\":\"China (中国)\"},\"city\":{\"type\":\"text\",\"data\":\"海淀区\"},\"address\":{\"type\":\"text\",\"data\":\"123\"},\"postalCode\":{\"type\":\"text\",\"data\":\"10010\"},\"documentType\":{\"type\":\"select\",\"data\":\"1\"},\"residenceProofType\":{\"type\":\"select\",\"data\":\"bankStatement\"},\"front\":{\"key\":\"aa66252f39c347bba64e52a51639dfd7.png\",\"url\":\"//ink-assets.oss-cn-beijing.aliyuncs.com/license-ocr/aa66252f39c347bba64e52a51639dfd7.png\",\"type\":\"image\"},\"back\":{\"key\":\"d9b259c09f204fa49716c9ac0cb2b002.png\",\"url\":\"//ink-assets.oss-cn-beijing.aliyuncs.com/license-ocr/d9b259c09f204fa49716c9ac0cb2b002.png\",\"type\":\"image\"},\"handheld\":{\"key\":\"02e111bbe38044b49a1a23880f8c6558.png\",\"url\":\"//ink-assets.oss-cn-beijing.aliyuncs.com/license-ocr/02e111bbe38044b49a1a23880f8c6558.png\",\"type\":\"image\"},\"bankStatement\":{\"key\":\"243d4681d65c4bf0b999f0deb27fcc8e.jpg\",\"url\":\"//ink-assets.oss-cn-beijing.aliyuncs.com/license-ocr/243d4681d65c4bf0b999f0deb27fcc8e.jpg\",\"type\":\"image\"}}",
  "extraData": null,
  "description": null,
  "extension": null,
  "kycCreatedDate": "2018-11-09T03:48:31Z",
  "kycLastModifiedDate": "2018-11-09T18:49:11Z",
  "authorityName": [
    "ROLE_ADMIN,ROLE_USER"
  ]
}
```

* **异常情况：无**

#### 4.根据 userId 数组查询用户

```
GET    http://localhost:8080/user/ids/1,2,3,4,5
```

* **接口说明：**
  * **只返回 User 信息和用户相关权限**
* **参数说明：**
  * **Long \[ \]  userId 数组**
* **返回结果：**

```
[
  {
    "id": 1,
    "email": "system@localhost.com",
    "mobile": "+86-10000",
    "inkId": "1000",
    "areaCode": "+86",
    "firstName": "System",
    "lastName": "System",
    "imageUrl": "",
    "activated": true,
    "langKey": "en",
    "createdBy": "system",
    "createdDate": "2018-09-08T15:49:48Z",
    "lastModifiedBy": "system",
    "lastModifiedDate": null,
    "authorities": [
      "ROLE_USER",
      "ROLE_ADMIN"
    ]
  },
  ......[other data]
]
```

* **异常情况：无**


