基于jQuery的整屏切换效果，支持chrome，firfox，IE（6-new）；

###update2015/6/18  IE8,7滚动距离无法取值；

###update2015/6/10  修移动端复step异常；

###配制方法（以test.html为例）
        var onepage = $("#box").onepagescroll({
            box: "div",                      //窗口选择器 jq选择器 
            cycle: 0,                         //是否循环滚屏 IE9（含）以下不支持  默认循环 【可选】 
            animationTime:0.8,    //滚动持续时间 单位秒 默认0.8s 【可选】
            disance:100                 //触摸滑动的最小距离 单位px  默认100  【可选】
        }, function (o) {               //滚动回调  【可选】
            ...【1】
        });
        
###添加滚动标记的方法（以test.html为例）
接着上方【1】滚动回调：<br/>

        $("#contorl .on").removeClass("on");
        $("#contorl span").eq(o.index).addClass("on");
        
滚动之后的返回值o（名字自定义），数据内容：<br/>

        index: 当前窗口的角标
        viewbox: 当前窗口的jq对象
        
注：窗口内部的子元素需要点击或其他事件，例如a的超链接，请在回调中写入禁止冒泡

###外部手动滚动的方法（以test.html为例）
利用右侧的标记，为其绑定click事件<br/>

        $("#contorl span").click(function(){
            onepage.change($(this).index());        //调用返回值的change方法 传入当前需要被切换的窗口角标
        });

        
