# jquery.zclip 使用介绍

复制页面内容到剪贴板兼容各浏览器 http://steamdev.com/zclip/


----------


##引用方式

	require('jquery-zclip');

##使用方法

	$('#copy_input').zclip({ 
        path: __uri('../../components/jquery-zclip/ZeroClipboard.swf'), 
        copy: function(){//复制内容 
            return $('#mytext').val(); 
        }, 
        afterCopy: function(){//复制成功 
            $("<span id='msg'/>").insertAfter($('#copy_input')).text('复制成功'); 
        } 
    }); 

##参数说明
- path：swf调用路径，必须，如js/ZeroClipboard.swf，ZeroClipboard.swf文件已存在下载包中。
- copy：复制的内容，必须，任意字符串，也可以是回调函数返回的内容
- beforeCopy：复制内容前回调函数，可选
- afterCopy：复制内容后回调函数，可选


##提供了3个方法:
- show:$(selected).zclip('show');//复制功能有效
- hide:$(selected).zclip('hide');//复制功能无效
- remove:$(selected).zclip('remove');//完全移除复制功能


##注意点



值得注意的是如果是复制的内容来自输入框input、textarea等，copy对象使用：

	copy: function(){ 
	    return $('#mytext').val(); 
	} 

如果是复制的内容来自页面元素div、p之类的，copy对象使用：

	copy: $('#mytext').text();


官方原文
    
	> /* zClip is a flash overlay, so it must provide */
	> /* the target element with "hover" and "active" classes */
	> /* to simulate native :hover and :active states. */
	> /* Be sure to write your CSS as follows for best results: */
	> 
	> a:hover, a.hover {...}
	> a:active, a.active {...}

翻译后就是说，zclip支持a标签的hover和active效果，但需要把:hover修改为.hover，:avtive修改为.active，因为zclip会在hover a标签的时候自动加上hover类，在active的时候自动加上active类。所以这么写是最好的：


	zclip{
		background:#eee;
	}
	zclip:hover,zclip.hover{
		background:#ddd;
	}
	zclip:active,zclip.active{
		background:#888;
	}













