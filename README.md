# rich-plugin 使用指南

### 使用

1. 在微信小程序管理后台，按 APPID `wx1e65af34b173feb0` 搜索到该插件，并点击添加，即可在代码中使用 `rich-plugin` 了

```json
"plugins": {
  "wxparserPlugin": {
    "version": "1.0.0",
    "provider": "wx1e65af34b173feb0"
  }
}
```

2. 在需要使用到该插件的小程序页面的 `json` 配置文件中，做如下配置：

```json
{
  "usingComponents": {
    "wxParser": "plugin://wxparserPlugin/wxParser"
  }
}
```

4. 使用

```html
<wxParser rich-text="{{richText}}" />
```

### 组件属性介绍

- rich-text: 你的富文本字符串
- bind:tapImg: 监听图片点击事件，通过 e.detail.src 可拿到图片地址
- bind:tapLink: 监听链接点击事件，由于微信小程序插件的限制，目前无法在插件中使用 wx.navigato 等跳转链接接口，开发者如需使用链接跳转功能，可在该事件的监听函数中操作

具体使用

```html
<wxParser rich-text="{{richText}}" bind:tapLink="goto" />
```

```js
goto: function(e) {
  wx.navigateTo({
    url: e.detail.href
  })
}
```

注：由于小程序的限制，链接必须为你的小程序中的页面的路径。
