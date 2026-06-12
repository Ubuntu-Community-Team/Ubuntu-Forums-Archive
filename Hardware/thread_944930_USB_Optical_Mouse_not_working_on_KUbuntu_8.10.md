---
title: "USB Optical Mouse not working on KUbuntu 8.10"
date: 2008-10-11
forum: Hardware
---

### Post by Muhammad A Siddique on 2008-10-11
Hello!

I've just installed KUbuntu 8.10 on my HP-Compaq 6720s. Everything is working fine except for my usb-optical mouse, which is 'lit' but not working at all. The mouse is okay, as I've checked it on Windows XP.

I've been surfing the net for solutions in this regard, but since I'm a beginner on Ubuntu/Linux, I make very little out of it. I request for assistance, and that do adapted for an amateur like me.

Thanks

M A Siddique

---

### Post by prshah on 2008-10-12
> **Muhammad A Siddique said:**
> 
I've just installed KUbuntu 8.10 on my HP-Compaq 6720s. Everything is working fine except for my usb-optical mouse, which is 'lit' but not working at all. The mouse is okay, as I've checked it on Windows XP.


Try starting up the computer with the mouse plugged in; does it work then? 

I _think_ hot-plugging some (cheapo) mice is a little problematic, but can be handled; however, we need to know that the mouse works in (K)ubuntu, hence the above workaround; if that works, we can troubleshoot further.

Additionally, open a terminal (Applications-Accessories-Terminal) and give the command```
lsusb
``` and post the output here for additional details.

---

### Post by Sef on 2008-10-12
1) Do you dual boot XP?   

2) Have you changed the usb port the mouse is plugged in?

---

### Post by lin108805 on 2008-11-03
I got same condition in Ubuntu 8.10. My IBM Thinkpad t43 trackpoint works fine, but usb mouse that plug in usb hub doesn't work. If I replug usb mouse, then it can work.

---

### Post by fishtron on 2009-01-12
I have a similar problem on my Acer Aspire One with a BenQ M310. This is my lsusb output:

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0d62:1000 Darfon Electronics Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The mouse is the Darfon one.

I've tested it in xev and I found that all the buttons and the scroll wheel work, but it doesn't detect any movements.

Hot-plugging it doesn't work; booting with it doesn't work; I've tried all three available ports. It works on my Windows machine at work. I will try if it works in Hardy or on a livecd.

My friend's Logitech wireless mouse works with hot-plugging. :(

I've edited the xorg.conf to add a device (which worked for the extra buttons on Hardy!) but it didn't work this time. I've since read that I should be using HAL instead, in Intrepid. any pointers!

---

### Post by dghenke on 2009-02-04
I have the same problem (only on 8.10; 8.04 works fine). It does not matter if the mouse is plugged in at boot time, if it is a cold or warm boot, or if I unplug and re-insert the USB dongle.

I've filed a bug report with more detailed information here:
   [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/325581](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/325581)

If you're reading this much after 04 Feb 2009, and you find no joy in this thread, check the above link for solutions.

---

### Post by abn91c on 2009-02-04
what brand mouse? did yopu switch to different USB ports, my Dell PC has an HP model 5188-2466 rev A optical mouse and it works normally.

---

### Post by wolfgentleman on 2013-01-04
I have 2 USB mice and one PS2 mouse. The PS2 works, the 2 USBs don't.

---

