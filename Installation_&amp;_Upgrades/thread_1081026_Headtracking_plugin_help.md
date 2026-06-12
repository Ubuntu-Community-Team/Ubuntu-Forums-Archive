---
title: "Headtracking plugin help"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by jo282 on 2009-02-26
As they closed the tread of the headtracking plugin i open a new thread to get some help

I installed OpenCV and now i need to compile the headtracking plugin...When i try to compile it give me an error :

> build/headtracking_options.c:859: warning: implicit declaration of function ‘compFiniDisplayOptions’
build/headtracking_options.c:859: warning: nested extern declaration of ‘compFiniDisplayOptions’
build/headtracking_options.c: At top level:
build/headtracking_options.c:864: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘headtrackingOptionsInit’
build/headtracking_options.c: In function ‘headtrackingOptionsFini’:
build/headtracking_options.c:881: error: ‘headtrackingPluginVTable’ undeclared (first use in this function)
build/headtracking_options.c:882: warning: ‘return’ with a value, in function returning void
build/headtracking_options.c:885: warning: implicit declaration of function ‘freeDisplayPrivateIndex’
build/headtracking_options.c:885: warning: nested extern declaration of ‘freeDisplayPrivateIndex’
build/headtracking_options.c: At top level:
build/headtracking_options.c:896: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
make: *** [build/headtracking_options.lo] Error 1

Please help me ! I dont get any answer on the compiz forum.

Thanks !

---

### Post by Rhubarb on 2009-02-26
I'm not familiar with openCV (now that I've looked it up, it does indeed look quite promising), but I know from a year ago there was a head tracking plugin for compiz that used a wiimote and 2 IR LEDs.
I don't think this project is maintained, and hence may not be able to be compiled for an up-to-date compiz install.

To be honest, I don't even know that there is a head tracking plugin that uses openCV.

For the benefit of others and myself, could you please post some links to the compiz plugin and any other relevant openCV URLs?

Then perhaps there may be someone who may be of assistance to you.

-Rhubarb

---

### Post by jo282 on 2009-02-26
Here`s a link... They closed the thread yesterday

[http://ubuntuforums.org/showthread.php?t=952895]("http://ubuntuforums.org/showthread.php?t=952895")

Thanks !

---

### Post by Rhubarb on 2009-02-28
Well,

Looking at the thread here:
[http://forum.compiz-fusion.org/showthread.php?t=9746&page=12](http://forum.compiz-fusion.org/showthread.php?t=9746&page=12)

The relevant post:
[http://forum.compiz-fusion.org/showpost.php?p=71390&postcount=117](http://forum.compiz-fusion.org/showpost.php?p=71390&postcount=117)

If you wish to install the compiz dev packages, you can do it thus:
```
sudo aptitude install compiz-dev
```

If this doesn't work, try installing all the relevant compiz dev packages:
```
sudo aptitude install compiz-dev libcm-dev libcompizconfig0-dev libdecoration0-dev
```

You may have to get it from SVN, which is the most up-to-date way of grabbing the latest compiz apps.
I can't elaborate on this, as I haven't tried out this plugin myself (though it does sound really quite nice).

-Rhubarb

---

