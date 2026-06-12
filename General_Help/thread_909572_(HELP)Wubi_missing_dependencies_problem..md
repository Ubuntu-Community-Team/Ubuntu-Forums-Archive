---
title: "(HELP):Wubi missing dependencies problem."
date: 2008-09-03
forum: General Help
---

### Post by busta5000 on 2008-09-03
I just installed the latest wubi but it has some missing files I am trying to connect my ubuntu hardy to my wireless usb adapter linksys WUSB300N. these are the list of needed files & their dependencies:
debhelper -> dpkg-dev
dpkg-dev  -> patch
patch     -> failed thouggh no dependencies
libaudio2 -> failed to install though no dependencies
ndisgtk -> ndiswrapper-utils-1.9
ndiswrapper-utils-1.9 -> ndiswrapper-common
ndiswrapper-common -> failed to install though no dependencies
ndiswrapper-source -> debhelper
WUSB300N -> ndiswrapper

so u see ndiswrapper-common & libaudio2 failed to install so how can I install all the rest each file depends on the other & 2 failed so I can't do anything I'm stuck with no internet connection because the ones who failed are required for ndis so I can't install my driver with no ndiswrapper.  I installed all these from th ubuntu site & ndiswrapper site I installed the most recent releases. so there are no missing files I downloaded everything why did ndiswrapper-common failed though it has no dependencies the same thing goes with libaudio2. so I hope you help me.

---

### Post by MsTBSoX on 2008-09-03
[font=Arial][[size=3][color=red]In 2008 Beijing Olympic Games[/color][/size]](http://wangluozhuanqian.org)[color=silver][size=1] Britain sports delegation has made the [/size][size=1]cmmings[/size][/color][/font][font=Arial][size=1][color=silver] historical progress, wins 19 golden 13 silver 15 copper altogether [/color][/size][/font][[font=Arial][size=1][color=silver]**12530**[/color][/size][/font]](http://12530-12530.net)[font=Arial][size=1][color=silver]medals, [/color][/size][/font][[font=Arial][size=1][color=silver]**cmmings**[/color][/size][/font]](http://cmmings.cn/)[font=Arial][size=1][color=silver] arranges in gold medal announcement 4th, and breaks two [/color][/size][/font][[font=Arial][size=1][color=silver]**world**[/color][/size][/font]](http://wangluozhuanqian.org/)[font=Arial][size=1][color=silver] records. Had the historical leap as [/color][/size][/font][[font=Arial][size=1][color=silver]**12530**[/color][/size][/font]](http://12530-12530.org)[font=Arial][size=1][color=silver] Olympic Games host country Britain sports.[/color][/size][/font]

---

### Post by juanpecan on 2008-11-11
did you solve this issue? i want to upgrade to 64 bit 8.10 but want to be sure the wusb300n will work on it.

---

