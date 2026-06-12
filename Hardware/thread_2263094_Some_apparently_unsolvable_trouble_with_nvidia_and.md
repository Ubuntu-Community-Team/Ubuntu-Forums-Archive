---
title: "Some apparently unsolvable trouble with nvidia and wide screen 21.5"
date: 2015-01-29
forum: Hardware
---

### Post by jerome72 on 2015-01-29
Hi guys, I come here after many vicissitudes about the correct work of my nvidia geforce 9500gt setting monitor resolution. Indeed, the desktop graphic interface of xfce does not utilize the total wide screen (21.5 inchs).

Story: at the beginning, it gives me a black-screen at boot of desktop, after the installation of nvidia proprietary drivers. I solved this problem with bumblebee, but wide screen does not still work. I complied with some tutorials to adjust the monitor settings, but all this methods run into some fail. I report few of this hitch:

xrandr
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm

```

xrandr | grep connected
```
xrandr: Failed to get size of gamma for output default
default connected 1280x1024+0+0 0mm x 0mm

```

sudo X -configure
 [ATTACH=CONFIG]259590[/ATTACH]


It seems that I have to configure totally manually the xorg.conf file. But I don't understand how it work: how the boot decide to read it or not?
The system read the empty sectors of the file .conf causing errors or replace empty sectors with an automatic procedure of configuration, or even ignore the entire content of the file .conf if some is uncorrect or empty?
Someone may kindly help me to solve this problem or at least to understand it?

Thanks :)

---

