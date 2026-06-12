---
title: "Toshiba Satellite Pro L20 ATI fglrx driver problems"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by jbreen on 2006-06-10
I have a Toshiba Satellite Pro L20 running Ubuntu 6.06 happily, and recently needed to make use of the acceleration on its video card (ATI Radeon XPress 200M).  So, I installed the xorg-driver-fglrx and fglrx-control packages and set up X to use the driver and everything seemed to work fine.  

After I had finished with the program that used the OpenGL support, I noticed that my wifi was no longer connected.  I ran the script I use to scan for available wireless networks and log me in to a known one, and got a message that scanning was not supported on that interface.  From a shell I tried resetting the interface and manually scanning for networks, with the same effect.  I eventually had to reboot, after which my network came back.

The network this time stayed available for 5 minutes or so then disappeared again.  On the next reboot, it stayed up for 8 hours before disappearing.

I downloaded the kernel module source package and compiled that against my installed kernel, thinking that might fix the problem, but it still persists.

The external USB mouse and keyboard I use with the laptop have also started to display similar behaviour - locking up and refusing to work.

I dont' know what's happening - but it seems likely that the ati driver is causing networking and usb to shut down under ubuntu.  I;m sure it's not the laptop - it's only a few months old and I've never had problems like this with it before.

Help if you can, or at least confirm that you have experienced the same issues!

JB

---

