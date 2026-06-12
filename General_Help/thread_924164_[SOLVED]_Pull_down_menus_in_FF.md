---
title: "[SOLVED] Pull down menus in FF"
date: 2008-09-19
forum: General Help
---

### Post by acron1 on 2008-09-19
Hi all,
This is something that has been bothering me ever since I started using FF.
The "pull down menus" are hidden behind other parts of the web page see below:

[IMG]http://i33.tinypic.com/smg840.png[/IMG] 

Thanks for your help.

---

### Post by anotherdisciple on 2008-09-19
Strange... does this happen on all websites?

---

### Post by anotherdisciple on 2008-09-19
I just went to that exact same URL >> [http://www.sharkeyextreme.com/hardware/cpu/article.php/3261_3742726__10](http://www.sharkeyextreme.com/hardware/cpu/article.php/3261_3742726__10)

and I didn't see that toolbar at the top?!?! Is it an add-on?

---

### Post by Elfy on 2008-09-19
I don't see it either, but I do in opera and it works properly. Might be a flash problem I think.

---

### Post by acron1 on 2008-09-19
Hi Anotherdisciple and yes this happens to all websites that have flash and that bar is always there. I am including pics from another PC I use.

[IMG]http://i34.tinypic.com/282eudd.png[/IMG]

2nd pic

[IMG]http://i38.tinypic.com/wlzqjl.png[/IMG]

If you look closely at the second pic you will notice that the menu for 
"CNET tech shows" is seen above and below the flash player BUT not on it as it should. This is most likely a flash problem and I am surprised no one else is bothered by it as it happens on all my Linux machines (Ubuntu, Fedora and openSUSE) running FF so I would think it's happening on many other PCs. I am going to check if it happens with Opera next and report back.
Thanks for your help

---

### Post by acron1 on 2008-09-19
Forestpixie you said you had no problem using Opera?
It appears to be the same for me even with Opera:

[IMG]http://i36.tinypic.com/qsuk4k.png[/IMG]

Does anyone have any ideas? Does anyone else have this problem?

---

### Post by Elfy on 2008-09-20
Maybe reinstall flash then - either the repo version or the adobe

The version in the repos can be ```
sudo apt-get install flashplugin-nonfree
```

I have also had to install libflashsupport to get sound with pulseaudio

You can also get it from adobe
download the .tar from [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
Installation - [http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

---

### Post by mb_webguy on 2008-09-20
A better solution would be to install the Flash 10 plugin from the backports repository, and make sure libflashsupport is *not* installed.  The Flash 10 plugin (supposedly and apparently) fixes the problems that libflashplugin was intended to patch.

Yes, the menu problem is due to either a bad rendering of Flash content (or sometimes Javascript or CSS), bad implementation of Flash content (or sometimes Javascript or CSS), or both.  The rendering issue you can improve by using a browser and plugins that do a better job of rendering that content.  Firefox 3 does a very good job of rendering Javascript and CSS.  The official Flash plugins tend to do a better job of rendering Flash content than the open-source versions (unfortunately), and each new version of the Flash plugin (theoretically) renders Flash better than the previous version.

Unfortunately, you can't do anything about bad implementation.  A badly-coded menu is going to act funky no matter what you do.

---

### Post by acron1 on 2008-09-20
> **mb_webguy said:**
> A better solution would be to install the Flash 10 plugin from the backports repository, and make sure libflashsupport is *not* installed.  The Flash 10 plugin (supposedly and apparently) fixes the problems that libflashplugin was intended to patch.

Yes, the menu problem is due to either a bad rendering of Flash content (or sometimes Javascript or CSS), bad implementation of Flash content (or sometimes Javascript or CSS), or both.  The rendering issue you can improve by using a browser and plugins that do a better job of rendering that content.  Firefox 3 does a very good job of rendering Javascript and CSS.  The official Flash plugins tend to do a better job of rendering Flash content than the open-source versions (unfortunately), and each new version of the Flash plugin (theoretically) renders Flash better than the previous version.

Unfortunately, you can't do anything about bad implementation.  A badly-coded menu is going to act funky no matter what you do.


Thanks a bunch Mb_webguy this worked like a charm.

[IMG]http://i36.tinypic.com/2dwerg0.png[/IMG]

---

### Post by tonyscha on 2008-09-21
Is there any fixes for users using flash 9 yet? I have found serveral websites I am having this issue on.

Edit: I disable all my plugins, so its not any of those that are causing the issue. I have include a screenshot of walmarts website doing the same problem.

---

