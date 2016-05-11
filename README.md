# js<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>参数的值-引用类型-引用传递-案例-对象值的合并</title>
</head>

<body>
   <script type="text/javascript">
      
	  function showBookInfo( book){
		 var defaultvalue={
		    name:'未知书名',
			pages:0,
			author:'zy'
		};
		book=mergeObject( defaultvalue,book);      //调用mergeObject函数，完成将defaultvalue和book值合并到一起过程
	     document.write("书名:"+book.name+"&nbsp;"+"页数 ："+book.pages+" 作者："+book.author+"<br/>");
	}
	
	//合并两个对象的值，如果realvalue中没有这个属性,则采用defaultvalue中的值，有，则使用realvalue中的值
	//返回一个对象
	function mergeObject( defaultvalue, realvalue){
	    if( realvalue && typeof realvalue=='object'){
	       for(var key in realvalue){      //name   pages    key通过键取出值
		      defaultvalue[key]=realvalue[key] || defaulevalue[key];   //realvalue['name'] => 'java深入钱出'   realvalue['pages']=>500
			  /*if( realvalue[key]){
			    defaultvalue[key]=realvalue[key];
			  }else{
			     defaultvalue[key]=defaultvalue[key];
			   }*/
		   }
		}
		return defaultvalue;
	}
	
	var book1={ name:'java深入钱出',pages:500};
	showBookInfo( book1);
	
	var book2={ name:'js'};
	showBookInfo( book2);
	
	function showStuInfo( stu){
	  var defaultvalue={
	   name:'张三',
	   age:18,
	   gender:0
	  }
	  stu=mergeObject( defaultvalue,stu);
	  document.write("姓名："+"&nbsp;"+stu.name+"&nbsp;&nbsp;"+"年龄："+"&nbsp;"+stu.age+"&nbsp;&nbsp;"+"性别："+(stu.gender==1?'男':'女')+"<br/>");
	}
	
	/*function mergeObject( defaultvalue,realvalue){
	   if(realvalue && typeof realvalue=='object'){
		  for(var key in realvalue){
		     defaultvalue[key]=realvalue[key]  ||  defaulvalue[key];
		  }
		}
		return defaultvalue;
	}*/      //这一段没必要重复，上面有可直接用
	
	var stu1={ name:'李四', age:20};
	showStuInfo( stu1);
   </script>
</body>
</html>
