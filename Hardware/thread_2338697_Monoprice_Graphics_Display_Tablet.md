---
title: "Monoprice Graphics Display Tablet"
date: 2016-09-30
forum: Hardware
---

### Post by Daedal on 2016-09-30
So i recently bought a MonoPrice 22" Graphics display tablet off of massdrop.com  ( [http://www.monoprice.com/product?p_id=14481]("http://www.monoprice.com/product?p_id=14481") )
as you can see in the description blurbs it mentions having linux support in a few different places. 
i didn't want to go off of just that though so i kept searching around the internet for any information i could find about it working in linux but aside from where it says it has linux support all i could find was a reply to an amazon review that mentioned it working well with a RasPi running raspbian and testing it with mypaint just plug and play and didn't have some of the issues they were having with it in windows. i can't seem to find the comment again but what i really wanted this for was my desktop.
the screen looks pretty nice and it works well in krita on windows10 but i don't use windows much. in ubuntu the screen still works as you'd expect but the graphics tablet functions are not responsive at all.

anyone wanna help me out here?

lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
_**Bus 007 Device 004: ID 0b57:9016 Beijing HanwangTechnology Co., Ltd **_
Bus 007 Device 003: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02
Bus 007 Device 002: ID 1c57:1e45  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 001 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102/2.0 / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 7545:109a  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

bolded and highlighted what i think is the important part of that... not sure where to go from here  pretty much just an end user.

---

### Post by Daedal on 2016-09-30
some links that lead me to believe there's plenty of hope aside from the fact that a lot of these non-wacom tablets (bosto, monoprice, etc) use the same digitizers and others have gotten theirs to work.

[http://forum.bosto.co/viewtopic.php?t=1140](http://forum.bosto.co/viewtopic.php?t=1140) also using hanwang tablet devices.
[http://forum.bosto.co/viewtopic.php?t=1246](http://forum.bosto.co/viewtopic.php?t=1246) same issue as i'm having but they got it fixed.  not entirely sure if the bosto scripts would work for me or how to use them.
[http://cateee.net/lkddb/web-lkddb/TABLET_USB_HANWANG.html](http://cateee.net/lkddb/web-lkddb/TABLET_USB_HANWANG.html) if i'm understanding that correctly then there's already some drivers for hanwang tablets in the kernel.

i'm fairly sure it's possible to get it working in linux i'm just not sure how.

---

### Post by MZ250Supa5 on 2017-01-16
I too am looking for a driver for a Parblo Coast 22, which also uses the Hangwang technologies digitiser, probably better known as Hanvon. I have a Hanvon tablet, and have had that working well under both Ubuntu and Manjaro - and the pen that comes with the Parblo works on the Hanvon tablet, so there can't be much to get these pen monitors working under Linux.

I'm going to try and use this neat script written for one of the Bosto tablets. 

[http://www.leslieviljoen.com/posts/18](http://www.leslieviljoen.com/posts/18)

I'll be using the driver script for the 14WA model, as I'm guessing the only reason there is a difference between that one and the one for the 22HD is that the 22HD has buttons in it, which of course neither the Monoprice nor the Parblo has. Once I've tried it, I'll post back here - but it may be a few days, as I'm in the middle of a major reorganisation at the moment, due, in part to the arrival of the Parblo Coast 22 (building new computer desk with multi monitor support etc), but I'm as eager as you to see if I can get this pen monitor working under Ubuntu and also hopefully other flavours of Linux.

As far as the directions go to install the Bosto drivers, it seems pretty much like the process for installing the Hanvon drivers, which is clearly outlined here, (and how I got my Hanvon tablet to work), courtesy of Favux's post of Sept 12th 2011:

[https://ubuntuforums.org/showthread.php?t=1178978](https://ubuntuforums.org/showthread.php?t=1178978) 

I don't know if Ondra Havel, the writer the Hanvon driver had any input into the development of the Bosto driver, despite there being several mentions of seeking their input it isn't clear if they responded or were actually involved. I may e-mail Ondra Havel and see if they can make any suggestions, as I know it can't be far our, as the pen from the Parblo functions as it should using the Hanvon tablet.

---

### Post by MZ250Supa5 on 2017-02-15
For people looking for a driver for a Parblo Coast 22 or a Monoprice 22 there is one that works, it can be found here:

[https://github.com/stacksmith/Monoprice_22_linux_kernel_module](https://github.com/stacksmith/Monoprice_22_linux_kernel_module)

Simply follow the directions in the README.md file and you're good to go. However, if you have an extended monitor/multiple monitor set up you will need to use this utility to be able to use your pen monitor: 

[http://wenhsinjen.github.io/ptxconf/](http://wenhsinjen.github.io/ptxconf/)

It works fine in test mode, but throws an error when issuing the install command. I've contacted the author of the utility, but am still waiting for a reply.

So far i've tested Gimp, MyPaint and Krita using this driver, and all work, with the exception of the eraser on the stylus, which isn't such a big issue if you use the Ctrl + Z keyboard combination, or in Gimp, which has an eraser tool anyway.

---

