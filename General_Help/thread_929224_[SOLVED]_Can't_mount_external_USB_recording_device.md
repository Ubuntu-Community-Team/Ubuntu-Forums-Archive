---
title: "[SOLVED] Can't mount external USB recording device"
date: 2008-09-24
forum: General Help
---

### Post by mastaphoo on 2008-09-24
Okay, my band just got done at a gig and the recording device has our whole show on it. I need to return it to its owner soon, and it just won't connect to my computer. I'm new to linux, btw.

It is a Roland R-1 ([http://www.roland.com/products/en/r-1/specs.html](http://www.roland.com/products/en/r-1/specs.html)). It usually used to just show up as an external drive similar to a USB drive on Windows, but my XP install died (RIP, not!). I tried going into terminal and doing **sudo fdisk -l**, but nothing showed up. Then, after forum surfing I tried **lsusb** command and I got this:

```
adm1n@Souluno:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 006 Device 002: ID 045e:009d Microsoft Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

```

The Logitech is my mouse and the Microsoft is my keyboard. Any clue how I can get this to connect? Thanks in advance.

---

### Post by mastaphoo on 2008-09-24
Nevermind.... Somehow, it worked the next time I tried. Ah well.

---

