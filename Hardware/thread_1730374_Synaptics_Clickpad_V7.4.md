---
title: "Synaptics Clickpad V7.4"
date: 2011-04-16
forum: Hardware
---

### Post by Kingcapone on 2011-04-16
Hey, 
 
In 10.10 my clickpad doesnt work just wondering if theres a chance of it working in 11.04 ?
 
I've done some research and havent found anything stating anythings going to change just thought it would be better to ask before I spend £1000 on a shiney new underpowered Macbook Pro, seem's like the only place to get %100 hardware support without the virus's!
 
Any help would be appreciated!
 
Thanks
 
P.S. 
My laptop's a HP DV7 4045ea!!!

---

### Post by Kingcapone on 2011-04-17
70 Views 0 Replys
Great.

---

### Post by bungernut on 2011-04-17
I have a HP tm2 and the answer is a resounding NO, clickpads do not work out of the box with 11.04 beta. 

This is very disappointing, and my solution is to run Ubuntu 10.04 in VirtualBox in windows.  

I wouldn't buy a macbook in anycase however...

---

### Post by jimmy the saint on 2011-04-17
Bug report

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809?comments=all](https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809?comments=all)

---

### Post by mörgæs on 2011-04-18
Does this help?

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by vedovatti on 2011-04-27
Hi there

I have a HP tm2 with clickpad multitouch.

Infact the clickpad doesnt work out of the box, but as a workaround you can install a the dkms-synaptics driver.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb)

It works (at least on the hp tm2), the two finger scrolling. And the right click (you have to click with two separated fingers at the same time, or a one finger click on the very right bottom corner). And the middle click (third button works!) click with 3 separated fingers or a one finger click on the very right top on the corner. 

By the way check the bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809) seems that Alexander finished a driver that works and with the led on off included. I havent test it but I it will work! Just check for updates on the bug, but seems that this clickpad finally will have a deceant driver.

---

### Post by vedovatti on 2011-04-27
.

---

