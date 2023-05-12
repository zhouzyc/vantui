# Transition 动画

### 介绍

使元素从一种样式逐渐变化为另一种样式的效果。

### 引入

在 Taro 文件中引入组件

```js
import { Transition } from '@antmjs/vantui'
```

## 代码演示

### 基础用法

- 将元素包裹在 transition 组件内，在元素展示/隐藏时，会有相应的过渡动画。
- transition 组件内置了多种动画，可以通过`name`字段指定动画类型。

```jsx
const animations = [
  'fade',
  'fade-up',
  'fade-down',
  'fade-left',
  'fade-right',
  'slide-up',
  'slide-down',
  'slide-left',
  'slide-right',
]
function Demo() {
  const [show, setShow] = react.useState()
  const animationAction = (ss) => {
    setShow(ss)
    setTimeout(() => {
      setShow(false)
    }, 1000)
  }

  return (
    <View>
      {animations.map((item) => (
        <Cell
          title={item}
          key={item}
          onClick={() => animationAction(item)}
        ></Cell>
      ))}
      {animations.map((item) => (
        <Transition
          duration={{ enter: 300, leave: 1000 }}
          className="center-x"
          enterClass="vanEnterClass"
          enterActiveClass="vanEnterActiveClass"
          leaveActiveClass="vanLeaveActiveClass"
          leaveToClass="vanLeaveToClass"
          key={`${item}tran`}
          show={show === item}
          name={item}
        />
      ))}
    </View>
  )
}
```

```css
.vanEnterActiveClass,
.vanLeaveActiveClass {
  transitionproperty: backgroundColor, transform;
}

.vanEnterClass,
.vanLeaveToClass {
  backgroundcolor: red;
  transform: rotate(-360deg) translate3d(-100%, -100%, 0);
}
```

### TransitionPropsCom [[详情]](https://github.com/AntmJS/vantui/tree/main/packages/vantui/types/transition.d.ts)

| 参数     | 说明 | 类型                         | 默认值 | 必填    |
| -------- | ---- | ---------------------------- | ------ | ------- |
| children | -    | _&nbsp;&nbsp;ReactNode<br/>_ | -      | `false` |
