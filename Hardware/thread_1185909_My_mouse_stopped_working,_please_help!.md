---
title: "My mouse stopped working, please help!"
date: 2009-06-12
forum: Hardware
---

### Post by Lacho on 2009-06-12
Hi,

Just yesterday my Microsoft USB Optical Mouse stopped working in my Laptop with Ubuntu 9.04, at first, I thought it was the battery, so I replaced it, but still no success, so I plugged it to the desktop, also with 9.04, and there it did work.

After reading several threads I could not find a definitive answer; tried to look for the saved state file, but could not find it even among the hidden ones, so I ran lsusb, and found that the mouse is recognized.

So What do you suggest?


horacio@turbo-penguin:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
horacio@turbo-penguin:~$

---

### Post by MauiKaren on 2009-08-07
Same thing happened to me.  I notice that the System76 drivers just updated on my Dart.

Hey - System 76  how do I UNDO the update and get my mouse back?

---

### Post by metalf8801 on 2009-08-07
while its unlikely that they both broke at the same time at least one of you should try to see if the mouse will work with another computer or with a live CD that doesn't have the update just to make sure this isn't a hardware problem 

just a thought 
Dan

---

