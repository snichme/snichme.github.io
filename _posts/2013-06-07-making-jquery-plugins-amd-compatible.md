---
layout: post
title:  Making jQuery plugins AMD compatible
date:   2013-06-07 15:00:00
tags:   JavaScript jQuery
---

The jQuery team has made it simple to write some code and extend jQuery with it, this is great and I think it is one of the features that has made jQuery so popular.

But this post is not about who to write a jQuery plugin, it is about how you can structure the code for your plugin to allow it to be used both as standalone and on a site that uses AMD.

This is how i structure all my jQuery plugins:
{% highlight js %}
(function (factory) {
  if (typeof define === 'function' && define.amd) {
    define(['jquery'], factory);
  } else {
    factory(jQuery);
  }
}(function ($) {
    $.fn.jqueryPlugin = function () {};
}));
{% endhighlight %}

*[AMD]:     Asynchronous Module Definition