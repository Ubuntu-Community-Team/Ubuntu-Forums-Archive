---
title: "USB mouse and USB keyboard not working"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by onequarterasian on 2008-01-18
whenever i live boot 6.06 Ubuntu on my desktop i can never use my mouse and keyboard which are both used via USB. ive tried on multiple hubs but the only USB that can be detected is my Cruzer Micro USB flash drive.

on the bootup it says checking mouse and keyboard and it says that its "ok"

my mouse and keyboard are both wired and 
keyboard- logitech classic keyboard 200
mouse- microsoft optical mouse blue

so for now im just stuck to live booting onto my laptop which runs slow


so any help would be greatly appreciated
andrew

---

### Post by dustman on 2008-01-19
i know i also had this problem. Try adding these parameters when booting the kernel ```
noapic irqpoll
``` It fixed the problem for me ;)

---

