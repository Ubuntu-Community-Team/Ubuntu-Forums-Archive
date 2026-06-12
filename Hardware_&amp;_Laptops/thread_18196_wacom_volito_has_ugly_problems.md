---
title: "wacom volito has ugly problems"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by doni on 2005-03-05
hi 

today i decided to paint. so i plugged in my wacom volito drawing pad (i've never done this in ubuntu before) and it seems to be working - somehow.

the ugly thing is that the mouse pointer doesn't really react as it should. it jumps around in the right upper edge and blinks kinda funny. it works to "press" a button and that stuff, but everything in the upper edge.

you may want to have a look at it so i recorded a [screen movie](http://telltec.ch/temp/wacom.mov) [2,3 MB MOV].
in the video i moved the pen over the pad from the right upper edge to the left bottom edge.

i downloaded the kernel source, made a symlink to /usr/src/linux and ran make menuconfig to see if wacom tablet support is activated in the kernel. and yes it is marked as a module.

any help? would be cool!

doni

---

### Post by p!=f on 2005-03-05
I'm not sure at all because I don't have any Wacom product by hand so I can't confirm if you'll find something useful on the link below. (HOWTO looks promising, though) :)
[http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)

---

### Post by Wombley on 2005-03-06
Theres some info on this problem at [http://www.ubuntulinux.org/wiki/WacomTabletIssue](http://www.ubuntulinux.org/wiki/WacomTabletIssue) , also many if you search the forums for "wacom" many people seem to have had the same problems, with various solutions. A while ago I managed to get a Wacom Favo (think its same as graphire series) basically working, havent worked much with it since though.

---

