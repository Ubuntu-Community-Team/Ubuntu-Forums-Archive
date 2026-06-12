---
title: "Lenovo S12 Screen Problem !"
date: 2009-10-04
forum: Hardware
---

### Post by haaamed on 2009-10-04
Hi,

I have installed ubuntu netbook remix on my laptop, however, the
screen get distorted in the beginning and the end of the installation
as well as the time that I am using it.
My netbook is a **Lenovo S12** having a high resolution (1280x800) windows
installed on it before the installation of ubuntu. The problem
persists even when I use ubuntu LIVE. It was not resolved after
changing the resolution nor the refresh rate.
I am using the monitor output of the netbook since the screen of the
netbook is not visible at all.
Below, you can see a snapshot of it.

I would be thankful if anyone can help me.

---

### Post by haaamed on 2009-10-09
I really need this fixed, wont somebody help?

---

### Post by magozoom on 2009-10-10
Hi!
I'm using Ubuntu 9.10 "Karmic" beta on my Lenovo S12 and I don't have any screen problems. Which version are you using - a lot of things were changed with the 9.10 release, specifically the graphics driver and the ext4 filesystems. Everything but hibernate is working great with 9.10
Attached screenshot from my S12
/magnus

---

### Post by jbfavre on 2009-10-10
Hello,
Had the same problem today.
As Lenovo S12 is shipped with VIA graphic card, you can solved it with: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Just compile and install last driver version.

No need to adapt or create xorg.conf.

Regards,
JB

---

### Post by yoshiki2 on 2009-11-05
Can you explain how to do that? that article is confusing...
I have the same netbook, am runing the live cd and it simply doesn't work.. do I need to install to mak eit work?

---

### Post by kiruri on 2010-05-05
yoshiki2, the solution works, you should simply start the alternate livecd like it is described [_here_]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Lenovo S12 (VIA Nano CPU based)") and then install the openchrome driver as jbfavre said.

---

