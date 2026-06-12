---
title: "External Drive Still Pauses"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by jimbo2150 on 2007-04-28
I had this problem with Edgy, figured it would be fixed in Feisty so I waited. I now have Feisty but am still having the problem.

I have an external WD hard drive and under high load it just pauses for like 15-20 seconds. It will continue to pause until any transfer is complete sometimes it occurs all the time (every minute or so), sometimes seldom (maybe every hour if watching a high-bit-rate video). I am not sure why or how to fix this. It never occured in Windows (tested it).

I searched the forum and could not find a similar posting. Anyone have any idea?

---

### Post by jimbo2150 on 2007-05-01
Ugh... After searching and searching...

I was getting those 'high speed usb device reset' errors after running dmesg.

Finally found it is a problem with what seems like data errors causing the high-speed USB driver to fail and reset the device when in high use. I removed the ehci_hdc module which reverted all USB ports back to version 1.1. It works now without interruption, but at a VERY SLOW speed (transfers that took 20 seconds now take minutes).

I hope this driver gets fixed soon, this is annoying.

---

