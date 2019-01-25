一、显示和定位
 元素显示方式display：在布局的时候显示类型强制转换；属性:none inline inline-block block
 元素的显示属性visibility：设置元素是否可见，即使不可见也会占据空间；属性 hidden visible
collapse（使用在表格元素时，用于删除一行或者一列，不会影响格局，所占据的行或者列会被其他内容试用，在其他元素上使用时显示为hidden）
代码css：
nput[type="text"][name="visibility"],
  input[type="text"][name="display"]{
    width:120px;
    margin-right:30px;
  }
  input[type="checkbox"]{
    width:20px; height:20px;
  }
  input[type="text"][name="visibility"]{
    visibility:hidden;
  }
      input:checked+input[name="visibility"]{
        visibility: visible;
      }
      imput[type="text"][name="display"]{
        display:none;
      }
      input:checked+input[name="display"]{
        display:inline-block;
      }
元素透明度opacity：表示方法从0到1可以保留两位小数
0和hidden都能是元素隐藏，区别是0能触发鼠标的悬浮
body{background:url(“../../../img/bgi/example-bgi-01.jpg”) no-repeat
     background-size:100% 100%;
     background-position:50%  50%;
     }
section{
     width:160px;height:160px;
     background:url(“../../../img/bgi/example-bgi-01.jpg”) no-repeat
     background-size:100% 100%;
     background-position:50%  50%;
     margin-right:20px;margin-top:20px;margin-bottom:20px;
     flaot:left;
     }
section:nth-child(1){opacity:0}
section:nth-child(2){opacity:0.2}
section:nth-child(3){opacity:0.4}
section:nth-child(4){opacity:0.6}
section:nth-child(5){opacity:0.8}
section:nth-child(6){opacity:1}
元素浮动float：该属性使元素脱离文档流，在父容器中进行浮动，停靠到父元素内容边界或其他浮动元素的边框，浮动的元素会忽略元素的空格，使同样焗油改属性的元素紧密的排列在一起；属性none left right
ul{
list-style:none;
margin:0;
padding:0;
}
ul.fl li,ul.fr li{
width:100px;
line-height:30px;
text-align:cemter;
color:#fff;
}
ul.fl li{
background-color:#ac0a0a;
float:left;
}
ul.fr li{
background-color:#0a36ac;
flaot:right;
}
注意：在普通的块级元素内的子元素全部都有浮动属性，那么自身高度就会是0像素
清除浮动副作用：
属性：
ul li{
width:100px;height:30px;
line-height:30px;
color:#fff
text-align:ceter;
}
section{
     width:960px;
     border:1px solid #ffff00;
    
section:nth-child(1) li{
background-color:#b20202
float:left;
}
section:nth-child(2) li{background-color:#b20202
float:right;
}
section:nth-child(3) li{background-color:#b20202
float:left;
}
.clear_left, .clear_right, .clear_left{height:0}
.clear_left{clear:left}
.clear_right{clear:right}
.clear_both{clear:both}
注意：消除子元素浮动会给页面添加一些无意义的空标签
使用绝对定位position：absolue
section{
     width:960px;
     border:1px solid #ffff00;
    
section ul{
position:absolute;
border:1px solid #ff00ff;
}
section:nth-child(2) li{background-color:#b20202
float:left;
}

section:nth-child(2) li{background-color:#b20202
float:right;
}
section:nth-child(3) li{background-color:#b20202
float:left;
}
剪切显示属性：overflow
是否剪切设定改属性元素对未能显示完全的内容，未能完全显示的内容是否在元素内生成滚动条以便于完全查看；还可以用老消除浮动元素对父级元素高度的影响；为了使父元素适应子元素的高度不能为visible
上面的代码的position:absolue改为overflow:hidden
注意：在二级导航条上剪切会导致根本不会显示
清除浮动影响的最佳方式：使用伪类元素选择器：after
section ul:after{
content:”.”;  //可以是空
height:0;
visibility:hidden;
display:block;
clear:both;
}
定位属性position：static(采用元素默认的定位方式) relative(对原始位置进行相对定位)：容易出现格式错乱（不会影响其他元素在文档流中的位置自己的位置也会保留）
 absolute(根据父元素进行绝对定位) ：
(在绝对定位是要设置高和宽)
元素会从“文档流”中脱离，不再占据页面内“文档流”的显示位置
“非块级”的元素会被转化成“块级元素”。
元素的宽和高将对内容自适应（不再是“块级元素”默认100%的宽度了）。
若一个具有宽和高的元素是其父级元素中唯一的子元素，并且其父元素没有设置高度属性，那父元素内容的高度将会变为“0”
fixed(相对于浏览器进行固定定位)：脱离文档流，和文档内的元素不会有布局上的干扰，而且不会影响其他浏览器的相对位置；适用：弹出框底部的“遮罩层    页面浮动二维码    “回到顶部”按钮   网站/应用操作指引    固定的顶部导航栏
例：
HTML：
<header>前赤壁赋</header>
<section>
  <article>...</article>
</section>
<footer>苏轼</footer>
CSS:
body:{
height:420px;
overflow-y:auter;
}
header,flooter{
width:100%;heught:50px;
background-color:#d40f0f;
position:fixed;
text-align:center;
font:32px/50px “全新硬笔行书简”,”楷体”;
color:#fff;
}
header{top:0;}
flooter{bottom:0;}
section{width:660px;
margin:0 auto;
padding; 60px,0;
}
article{
text-indent:2em;
font:26px “全新硬笔行书简”,”楷体”;
color:#620808;
}
