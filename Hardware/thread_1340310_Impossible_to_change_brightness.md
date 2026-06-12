---
title: "Impossible to change brightness"
date: 2009-11-28
forum: Hardware
---

### Post by Lurning on 2009-11-28
Hello,

I'm using an Acer Aspire Timeline 4810T-353g25Mn with a  GMA4500MHD.
My OS is ubuntu 9.10 and my desktop manager is Gnome 2.28.1

I've a problem with my brightness. I can't to change it. I have allways 100%.
My keybord shortcuts are working, I've have a notification when I use it, but  they don't works. 
If I unlpug the alimentation it is detect so I do not think it is a problem of acpi and  "xgamma -gamma 0.75" works



Pardon my English, I am French.
Thank you for help

---

### Post by tiddlydum on 2009-11-28
Same problem on Acer Aspire 5738. Ubuntu recognises brightness shortcuts, but screen brightness doesn't change. I'm running 9.04 x64

---

### Post by Lurning on 2009-11-29
I forgot to say that I use the i686 version

---

### Post by Lurning on 2009-11-29
I have display problems when I play sauerbraten or tuxracer so I think it's a graphics card problem

---

### Post by Lurning on 2009-11-29
Solution is in [https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

nomodeset acpi_backlight=vendor in grub

works with grub legacy

---

### Post by 1Myraj on 2009-11-30
I have a question similar to this.  My display brightness works and I have it at 0%  ...  but it's still not dim enough for me.  Eyes sensitive to light.  Is there an application or something in the settings I'm overlooking that will make my screen more dim than the brightness applet allows??

I have a Toshiba Satellite.

Thanks.

---

