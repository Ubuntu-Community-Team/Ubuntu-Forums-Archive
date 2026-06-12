---
title: "Trying to get backlight to work with psb driver on netbook"
date: 2009-12-20
forum: Hardware
---

### Post by gmatt on 2009-12-20
Hi,

I bought a MSI x260 ultra light (netbook) and so far everything is working pretty good, however, I can't adjust the backlight so my batterlife is much worse than it could be.


I have installed the psb driver (Poulsbo) as per [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

and everything works fine except backlight adjustment. 

I dug deeper into it and I downloaded the psb-kernel-source and I was looking through the source.


What is interesting is that I found that the code in intel_lvds.c checks to see what the blc_type is when the module is loaded. Throughout the code that manipulates backlight, the code checks to see if the blc_type is either 0x01 or 0x02 and acts accordingly, however, my blc_type is 0x00, which is why I don't have backlight support.

The two possible blc_types are defined as 

#define BLC_I2C_TPE 0x01
#define BLC_PWM_TYPE 0x02

. But I don't know what that means. Anyone have any idea how to get my backlight working? xrandr --ouput LVDS0 --set BACKLIGHT 50 does not work for me.

---

### Post by djtm on 2010-06-09
hey, did you ever find a solution? 

I guess one could try to force the setting to 0x01 or 0x02, but that could of course be risky.

I assume you also have no files in /sys/class/backlight/ ?

---

