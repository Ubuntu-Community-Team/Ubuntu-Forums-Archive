---
title: "Bluettoth in acer laptop problem"
date: 2009-10-29
forum: Hardware
---

### Post by pajus on 2009-10-29
Hello 
first sorry of my English...

I have a problem with bluetooth in my laptop (acer TM 2492nWlmi).
I have Ubuntu 9.04. i use gnome - Linux laptop 2.6.28-15-generic

When I start OS (after grub) system is loading.. but in one point of loading (i guess starting kernel) my devices - like webcam, wifi and bluetooth turns on... and it causes restart of computer... 
I've discoverd, that is cased by BT, because when I hold (physicly) button to trun off/on bluetooth adapter (it is in front of my notebook) system sometimes load normally.

So i need something to make bluetooth not starting while my os is loading...

I've tried - 
add btmodule into blacklist... it does nothing

add this: (this make by wlmi bluetooth off/on is is similar with wifi)
[html]echo 0 > /sys/devices/platform/acer-wmi/rfkill/rfkill1/state [/html]to rc.local but it doesnt help.

Really i need help in 9.04 it is ok because i can only hold the button and sometimes OS is loaded correctly, but sometimes. In 9.10 it doesnt work at all..

Thank you I really apersiate your help becouse I hopeless.

---

### Post by pajus on 2009-11-12
thx for answer:roll:

---

