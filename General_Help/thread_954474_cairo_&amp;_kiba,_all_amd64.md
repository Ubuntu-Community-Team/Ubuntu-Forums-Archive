---
title: "cairo &amp; kiba, all_amd64"
date: 2008-10-21
forum: General Help
---

### Post by loomsen on 2008-10-21
Here you are:

Cairo:
[cairo-dock-1.6.3.1](http://www.mediafire.com/?mzq0fxuxtk2)
[Mirror 1 (uploaded.to)](http://uploaded.to/?id=i5vi7m)

Kiba:
[kiba_8.62.01-1_amd64.zip](http://www.mediafire.com/file/wqyekt13t1m/kiba_8.62.01-1_amd64.zip)
Ignore the version, just a hint for me while building, as kiba isn't developed anymore anyway.

Enjoy

---

### Post by fab.head on 2008-11-09
Hi loomsen

Would it be possible for you to compile also the new cairo-dock 1.6.3 for amd64? and maybe also enable glitz?

Thanks a lot :D

---

### Post by loomsen on 2008-11-12
Up

---

### Post by fab.head on 2008-11-12
Great! Thanks

The link doesn't seem to work though...

Firefox says "Loading..." and nothing happens :(

Could you please check it?

Thanks a bunch

---

### Post by loomsen on 2008-11-12
OK, uploaded to upload.to too, seems like mediafire is down atm...

---

### Post by fab.head on 2008-11-12
You rock :)

Thanks a trillion

---

### Post by loomsen on 2008-11-12
So everything fine for u? Good :)

---

### Post by fabounet on 2008-11-12
hello
may I ask how you generated them ?

---

### Post by loomsen on 2008-11-12
Sure.

Started with the dock, 
```

./configure --prefix=/usr --enable-glitz
dh_make --createorig
dpkg-buildpackage

```

Then plugins
```

./configure && sudo checkinstall

```

And the themes like the dock with dh_make & dpkg-buildpackage.

---

### Post by skain on 2008-11-29
I'm using the version in the Hardy repos and would like to upgrade to this new package.

However, upon trying to install your package I'm getting a "dependency not satisfiable" error regarding libgtk2.0-0.

I checked synaptic and I have this package installed, any ideas?

I'm on AMD64 version of 8.04.1.

---

### Post by loomsen on 2008-11-30
No other idea than upgrading to intrepid... sorry.

---

### Post by victor.nn on 2009-02-10
Hi, this is my first post in this forum, I'm a beginner in linux,just started using ubuntu last week but I'm already very satisfied:P

I got the cairo-dock where it is working, but some effects are not available: on the tab views of the advanced mode there are no other options besides the default mode and a blank space for the main dock and sub-docks.
I can't put other views like 3d plane, carousel, parabolic, etc..
 

I figured my problem is something related to that post, but I'm not sure..
> **loomsen said:**
> Sure.

Started with the dock, 
```

./configure --prefix=/usr --enable-glitz
dh_make --createorig
dpkg-buildpackage

```

Then plugins
```

./configure && sudo checkinstall

```

And the themes like the dock with dh_make & dpkg-buildpackage.

I'm using Ubuntu 8.10 on an AMD64

Thanks !

EDIT: I solved my problem.. I'm sorry..
Thank you anyways :D

---

### Post by HippyRandall on 2009-02-18
I am really liking cairo-dock much more than kiba or AWN but I have one small issue. I cannot get the menu button in the dock to work. According to what I have read on the cairo-dock forums, I should be able to make a new launcher and in the command field put ```
<Alt>F1
``` to get the menu function but it doesn't work no matter what I have tried. 
Any ideas Loomsen?

Thanks,
Hippy Randall

---

### Post by loomsen on 2009-02-18
Sorry buddy, I haven't been using cairo for quite some time now.

I found this key tho in my gconf:

[[img]http://www.ubuntu-pics.de/thumb/9883/screenshot_100_002__UwuMVc.png[/img]](http://www.ubuntu-pics.de/bild/9883/screenshot_100_002__UwuMVc.png)

I also have this key:

[[img]http://www.ubuntu-pics.de/thumb/9884/screenshot_100_003__w9wjnf.png[/img]](http://www.ubuntu-pics.de/bild/9884/screenshot_100_003__w9wjnf.png)

You could also check if this key makes any difference:

[[img]http://www.ubuntu-pics.de/thumb/9885/screenshot_100_005__BxjLdO.png[/img]](http://www.ubuntu-pics.de/bild/9885/screenshot_100_005__BxjLdO.png)

Thats all I can say, hope it's somewhat helpful.

Another possibility would be the compiz-deskmenu.

I'm lovin it :)

Very handy and pretty easy to setup/configure.
[[img]http://www.ubuntu-pics.de/thumb/9886/screenshot_100_006__718MRr.png[/img]](http://www.ubuntu-pics.de/bild/9886/screenshot_100_006__718MRr.png)

---

### Post by HippyRandall on 2009-02-18
thanks for that compiz-deskmenu. works a charm! now to figure out how to get it into cairo as a launcher...lol

---

### Post by loomsen on 2009-02-19
Simply create a custom launcher and issue compiz-deskmenu as its command :)

Enjoy.
Works with gnome-panel so I guess it will work with cairo as well.

---

### Post by HippyRandall on 2009-02-21
I actually ended up installing the SVN beta2 version which has GMenu applet for a start menu option and some other neat features.

---

