---
title: "Problems installing with WPC11 v4"
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by s360 on 2006-06-25
Hi everybody,
I would like to install ubuntu on my old Think Pad. Sadly, the labtop doesn't have a LAN port and I've only got a linksys WPC11 v4 with it(connected to a unencrypted network). 
I tried installing on it but it failed on detecting network devices. After some searches on google/this forum, i know there's at least a method to get it works on a installed system. But is there any method so that I can load the WPC's driver before installing(and install the rest of all)?
The config of the thinkpad is as follow:
P2 233Mhz, 64Mb Ram, 10G harddrive
I'm new to the world of ubuntu/linux and would like to thank you all for helping.

---

### Post by K.Mandla on 2006-06-25
Hi. I have a WPC11 v3, and it's detected during installation and set up without a hitch. 

Even if you can't set up your network during installation you should be able to continue through (by escaping through the setup menus) and install Ubuntu. After everything is in place, you should be able to go back and work with your wireless and network once you have a GUI in place.

There are a couple of other things worth mentioning. First, take a look at this [thread]("http://www.ubuntuforums.org/showthread.php?t=125334") and see if the problems described there are similar to what you are experiencing. Older laptops seem to have trouble with the 2.6+ kernels, and if that's the case, you might have to move to a different distribution. Don't worry though, Zenwalk and Slackware are both great options, if you decide to try them.

The only other thing I can suggest is installing Xubuntu rather than Ubuntu, since a laptop that old is going to be burdened by Gnome and all the accessory stuff that's installed with straight Ubuntu. It's worth the time it takes to burn a second ISO, to get a smoother, faster desktop.

Good luck! Let us know how it goes.

---

### Post by s360 on 2006-06-26
thanks for your reply.
I finally got a PCMCIA LAN card from somebody else and finished the installation. Following your advice, I installed the Xubuntu instead of ubuntu-desktop and got my WPC11 v4 work by the method stated in </url>[This Thread]("http://www.ubuntuforums.org/showthread.php?t=95591&highlight=wpc11"). However, the performance is unacceptable, esp. when using Firefox, probably because of the low-memory.
Anyway, I would consider installing/using Ubuntu with my coming (faster) computer.

---

