#### autpro 使用问题

```
当在渲染页面的时候 遍历数组的时候 必须指定key  默认是找数组中的key键 代表唯一表示符号  如果是自己使用的id
直接指定rowKey={'id'}

const response = yield call(getData);  使用api方法时不要加括号调用

payload不能省略 
type 是要指定的方法 一般是使用  命名空间/方法名
*fetch({ payload }, { call, put })

在model里面 状态里面的数据类型是根据 api数据类型来设置的  数组的话state:[]   对象 state:{}  返回值也可以一致



import React,{Component} from 'react';
import Mytable from '../../components/Myzj/Mytable';
import {connect}  from 'dva';  引入connect


class Analysis extends Component {
  // 我们可以在组件加载时发送一个请求来获取数据。

componentDidMount() {
  const { dispatch } = this.props;
  dispatch({
    type: 'project/fetchNotice',
  });
  dispatch({
    type: 'activities/fetchList',
  });
  dispatch({
    type: 'chart/fetch',
  });
}继承父对象的构造函数
  constructor(props) {
      super(props);
  const {dispatch} = this.props;   使用dispatch都需要用connect 发送方法到model   action=>model
      dispatch({
        type:'mypro/fetch',
      });
  }
  render(){
    console.log(this.props);
    return (
      <div>
        <Mytable />
      </div>
    );
  }
}


export default connect( mypro => mypro )(Analysis);
```

#### 例子

```
我们可以在组件加载时发送一个请求来获取数据。
可以在生命周期方法中使用dispatch触发model里面的函数
componentDidMount() {
  const { dispatch } = this.props;
  dispatch({
    type: 'project/fetchNotice',
  });
  dispatch({
    type: 'activities/fetchList',
  });
  dispatch({
    type: 'chart/fetch',
  });
}
```

