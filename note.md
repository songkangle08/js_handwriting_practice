# JS 基础

## 原型/原型链

## new 关键字

new 一个对象，到底发生了什么？

- 1). 创建了一个对象，并把这个对象的原型链（**\_\_proto\_\_**）指向该构造函数的原型（**prototype**）
- 2). 调用该构造函数，并把该构造函数中的 this 指向这个新创建的对象
- 3). 判断该构造函数是否有返回值，如果有返回值并且返回值是对象或者函数的话，则返回该返回值，否则返回新创建的对象。

```javascript
function _new(Fn, ...args) {
  // 第一步
  /*
    const obj = {};
    obj.__proto__ = Fn.prototype;   // ie不能直接操作__proto__
  */
  // Object.create相当于上面的两句话
  const obj = Object.create(Fn.prototype);
  // 第二步
  const result = Fn.call(obj, ...args);
  // 第三步
  return (result != null && typeof result === "object") ||
    typeof res === "function"
    ? result
    : obj;
}
```

## instanceof 关键字
