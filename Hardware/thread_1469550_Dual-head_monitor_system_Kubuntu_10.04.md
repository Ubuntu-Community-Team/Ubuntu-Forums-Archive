---
title: "Dual-head monitor system Kubuntu 10.04"
date: 2010-05-02
forum: Hardware
---

### Post by devmstr on 2010-05-02
I have a notebook Asus V6X00V with 1400*1050 monitor(name: LVDS) and Dell Monitor 1920*1080 (VGA-0).
I want to have a dual monitor system. At MS Windows everything is working fine. During the Kubuntu installation the Dell and the main notebook monitors have a right resolutions(1920*1080 & 1400*1050). But after some stage it have been changed to the 1152*864 for both. Now the right resolution is only during turning off process and when I am using the console. So it shows that system can use this resolutions. The problem is just in a settings. 

I am using Size & Orientation - System Settings for setting adjustment. Any option that changes resolution for any monitor or changing position(Absolute, Left Of, Right of and so on) cause the color line noise on the screens. 

I have tried xrandr: 
```
xrandr --output LVDS --mode 1400x1050 --pos 0x0 --output VGA-0 --mode 1920x1080 --right-of LVDS --pos 1400x0
```
but have received the same result.

I have find out([http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)) that for example the previous version of Randr(1.2, now I have xrandr 1.3) need a xorg.conf file modification to create a big virtual screen, but kubuntu 10.4 don't have xorg.conf and I don't know should I modify xorg for 1.3 version of xrandr or not.

Please help me to solve this problem

---

### Post by jfelipe on 2010-05-11
Try to disable desktop effects.

System settings -> Desktop -> Desktop effects (first option on left column)

There, you can uncheck "Enable desktop effects". It usually solves several problems with compiz side-effects :)

Once you have done this, try to configure multiple-desktops with xrandr again (though I've found that using the "Screen" option in "System Settings" you can now configure everything from the desktop, and it works smoothly).

HTH.

---

