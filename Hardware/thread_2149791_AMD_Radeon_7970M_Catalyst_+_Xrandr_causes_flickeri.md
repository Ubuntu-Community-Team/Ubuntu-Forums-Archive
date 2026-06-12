---
title: "AMD Radeon 7970M Catalyst + Xrandr causes flickering screen"
date: 2013-05-29
forum: Hardware
---

### Post by dffx on 2013-05-29
I've been wrestling with getting the Catalyst drivers to work with my Enduro-powered laptop (7970M + Intel), and I've been able to install the Catalyst drivers successfully. However, whenever I enable the discrete card and login, and I attach an external monitor and try to span the screen across both monitors, I get intense flickering on both monitors. I took a quick video to show the result, as I've found it kind of difficult to describe:

[http://youtu.be/OHGIep3lvsg](http://youtu.be/OHGIep3lvsg)


This *only* happens when the desktop i spanning both monitors -- it works flawlessly when I'm just using 1 monitor, or have the monitor cloned. The Intel card can extend the desktop without any issue at all.

I followed these instructions to get the card working at all: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)

Does anyone know what might be causing this flickering?

Ubuntu 13.04 x64
Catalyst 13.6 beta
3.8.0-22-generic

Thanks!

---

### Post by dffx on 2013-05-30
Strangely enough, when I use the following xrandr command it works without any flickering at all:

> xrandr --output LVDS1 --auto --left-of HDMI1 --output HDMI1 --auto --scale 1.0001x1.0001

the tiny amount of scaling is not noticeable on my external monitor, and it *seems* to have removed any flickering of the screens. I don't really consider this to be a solution, however, only a sloppy work around.

---

### Post by g3n1uss-yandex on 2013-08-08
It seems the issue is caused by Xrandr. It cannot be disabled, even though you tell Ubuntu to disable it in configs,  nothing happens. So neither this command [FONT=Ubuntu Mono]sudo aticonfig --set-pcs-str="DDX,EnableRandR12,FALSE"[/FONT] either other ways do not work. The same with a new beta driver :( But thank you for this temporary solution!

---

### Post by emgiezet on 2013-11-30
You save my day!

I was fighting with this for 2 weeks. And get used to work on single external monitor!

THX!

---

