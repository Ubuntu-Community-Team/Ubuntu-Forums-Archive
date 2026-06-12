---
title: "Trouble with NVidia 7800 GT - blurry vertical lines over the screen"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by Pyntix on 2007-04-24
I've installed Kubuntu 7.04 (not x64) a few days ago, on this computer:
CPU: AMD Athlon 64 X2
Gfx: NVidia 7800 GT
HDD: 250 GB
RAM: 1024 MB

Earlier today I installed the NVidia drivers by following this HOWTO:

[http://cholito.org/2006/11/23/installing-nvidia-in-3-steps/](http://cholito.org/2006/11/23/installing-nvidia-in-3-steps/)

Before I installed it, I couldn't have a higher resolution than 1024x768. After I installed it, I can have it in 1280x1024 (as I want to) but there is a problem too.
Kubuntu doesn't fill out the whole screen, but leaves a black line at the right edge of the screen. The whole image is also about 10-20 pixels too far to the left. This causes the screen to have vertical "blurry lines" over the screen, where the pixels are pushed together because of the lack of space.

I've downloaded and tried to install the drivers from NVidias official website, but if I do it in the usual console, it wants me to turn off the X window system. I've tried both recovery mode and switching to runlevel 3 (which it suggested) without success,

Just so you know, I have hade a similar problem to this in Windows (where I just used the CD that came with the gfx card) and Fedora Core 6 (where I did the first thing mentioned [**here**](http://www.fedoraforum.org/forum/showpost.php?p=775701&postcount=2))

Here are some screenshots:
[http://img483.imageshack.us/img483/4025/skrmdump1vg1.png](http://img483.imageshack.us/img483/4025/skrmdump1vg1.png)
[http://img483.imageshack.us/img483/1353/skrmdump2gz4.png](http://img483.imageshack.us/img483/1353/skrmdump2gz4.png)
[http://img483.imageshack.us/img483/4020/skrmdump3jy1.png](http://img483.imageshack.us/img483/4020/skrmdump3jy1.png)

It's not very obvious but it's there, believe me. And don't mind the gray dots across the images, those are from the screenshot-program...

---

### Post by ziggykg on 2007-04-25
After installing the NVIDIA drivers did you update the Horizontal and Vertical sync ranges in your /etc/X11/xorg.conf file?  You can get these from your monitor's manual.

---

