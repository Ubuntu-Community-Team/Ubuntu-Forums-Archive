---
title: "Configure my acer Tablet pc (C310)"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by Cow03 on 2005-09-15
Hi everybody!!!!!!!!

First, sorry for the quality of my sentences, I'm french  ;-) .
Second, I need to install linux for university and I chose Kubuntu. I remember two years ago when I to install fedora core, it took 2 month for having a well configured OS, that the reason why I ask for help :). 

  There is the list of thing I want you to help:

1-change my root password (I've not assigned one yet )
2-Choose the correct monitor configuration cause there is a lot of noise when I move my mouse cursor through the desktop
3-Configure my wireless internet (LEAP authentification)
4-Enable the "Tablet pc" function with WACOM pilots (or whatever)

and what's in my laptop:

Intel Processor 2 GHZ
14.1 XGA TFT LCD
128MB NVIDIA GeForce Go 6200 w/turbocache
802.11 b/g wireless

Thanks a lot

SAm

---

### Post by prizrak on 2007-01-16
#1 No need, Ubuntu uses a sudo model. It will ask you for your user password anytime you try to do something that requires root priviliges and will atuo elevate you to root for that application alone.
#2 In terminal (w/e it is on Kubuntu)
```
sudo apt-get install nvidia-glx
```
```
sudo nvidia-xconfig
```
#3 No clue whatsoever never dealt with LEAP might not be possible under Ubuntu at this time
#4 ```
sudo apt-get install wacom-tools
```
There is a caveat here tho, the buttons won't work to rotate display. I made a how-to for right clicking and text input it's somewhere on the forum.

---

