---
title: "Can't get on after I enter my password"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by mrconfident on 2005-12-13
First off, hello to everyone, I'm new to this board and have seen alot of useful information here from all the members. I hope someone would be able to help me out with my problem.

I've always wanted to learn how to use linux. So after rading an article in Maximum PC i've decided to why not and give it a try.

So on with my problem....I've downloaded the 64bit version of ubuntu, burned the ifo to cd and completed the installion process.

My pc is a 3.2 640 processor, Nvidia 7800 GT vid. card and Dell 24" monitor. Durning the installion process when prompted to chose resolution I picked 1900 x 1200.

After rebooting and everything, I'm able to enter in my user name and password. Upon hitting "Enter" after typing in my password....I guess you can say the OS tried to load but for some reason I'm left with the brown background and a smaller darker brown box that looks like it tried to disply something but couldn't....and it comes to a halt....

I don't know what the problem is or how to even began seraching. Can someone please tell me what my problem is?

---

### Post by 23meg on 2005-12-13
You need to install the proprietary Nvidia drivers or switch to the vesa driver. To switch to vesa, change the "driver" line in the "Device" section of your /etc/X11/xorg.conf file to "vesa". To install the proprietary drivers, see [this thread]("http://www.ubuntuforums.org/showthread.php?t=75074").

---

