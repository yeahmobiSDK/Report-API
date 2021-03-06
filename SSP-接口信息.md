Cloudmobi Report API 使用指南
=== 

目录 
=== 


* [广告位层级报表](#广告位层级报表接口) 

* [国家层级报表](#国家层级报表接口) 
* [注意事项](#注意事项)
> 需要向ssp平台管理人员申请token才能访问接口


广告位层级报表接口
===

* 描述：ssp平台提供广告位报表按日拉取接口

* URL: http://www.cloudmobi.net/cloudmobi-reporting/index?t={token}&st={start time}&et={end time}

* URL示例: http://www.cloudmobi.net/cloudmobi-reporting/index?t={token}&st=2017-04-01&et=2017-04-03

* URL参数释义:  

|  字段   |   类型   |  说明   |
| :---: | :----: | :---: |
| token | string | token |
|  st   | string | 起始时间  |
|  et   | string | 截止时间  |

* 响应结果为**JSON数组**格式

* 响应结果字段列表 

|  字段   |   类型   |        说明        |
| :---: | :----: | :--------------: |
| error | string | 错误提示信息(成功返回空字符串) |
| data  | array  |     广告位信息对象      |

返回的广告位报表对象:

|     字段     |   类型   |  说明   |
| :--------: | :----: | :---: |
|   app_id   | string | 应用id  |
|  slot_id   | string | 广告位id |
|  revenue   | float  |  收入   |
|  request   | string |  请求数  |
| impression | string |  展示数  |
|   click    | string |  点击数  |
|    dau     | string |  日活    |
|  filled    | string |  填充数  |
|    day     | string |  日期   |


响应结果示例(示例数据，仅供参考)

  ```json 
{
    "error": "",
    "data": [
        {
            "app_id": "1",
            "slot_id": "2",
            "revenue": 888,
            "request": "88888888",
            "impression": "88",
            "click": "8",
            "dau": "6",
            "filled": "100",
            "day": "2017-04-01"
        },...
    ]
}
  ```

[Back to TOC](#目录) 


国家层级报表接口
=== 

* 描述：ssp平台提供广告位报表按国家、以日为单位拉取接口

* URL: http://www.cloudmobi.net/cloudmobi-reporting/country-report?t={token}&st={start time}&et={end time}

* URL示例: http://www.cloudmobi.net/cloudmobi-reporting/country-report?t={token}&st=2017-04-01&et=2017-04-03

* URL参数释义:  

|  字段   |   类型   |  说明   |
| :---: | :----: | :---: |
| token | string | token |
|  st   | string | 起始时间  |
|  et   | string | 截止时间  |

* 响应结果为**JSON数组**格式

* 响应结果字段列表 

|  字段   |   类型   |        说明        |
| :---: | :----: | :--------------: |
| error | string | 错误提示信息(成功返回空字符串) |
| data  | array  |     广告位信息对象      |

广告位信息对象:

|      字段      |   类型   |   说明   |
| :----------: | :----: | :----: |
|    app_id    | string |  应用id  |
|   slot_id    | string | 广告位id  |
| country_name | string | 国家国际代码 |
|   revenue    | float  |   收入   |
|   request    | string |  请求数   |
|  impression  | string |  展示数   |
|    click     | string |  点击数   |
|  dau       | string |  日活    |
|  filled    | string |  填充数  |
|     day      | string |   日期   |


响应结果示例(示例数据，仅供参考)

  ```json 
{
    "error": "",
    "data": [
        {
            "app_id": "1",
            "slot_id": "2",
            "country_name": "CN",
            "revenue": 888,
            "request": "88888888",
            "impression": "88",
            "click": "8",
            "dau": "6",
            "filled": "100",
            "day": "2017-04-01"
        },...
    ]
}
  ```
注意事项
===
* 数据拉取的时间范围不能超过7天（超过七天会返回错误），且只能查询最近90天的数据
* 所有报表数据以UTC 0时区统计
* 接口中返回的当日数据均不准确，在UTC 0时区 下一天的上午七点（UTC  T+1 7:00 AM）以后可取到准确数据，特殊情况除外。
