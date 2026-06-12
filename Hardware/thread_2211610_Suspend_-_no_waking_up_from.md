---
title: "Suspend - no waking up from"
date: 2014-03-16
forum: Hardware
---

### Post by michael-piziak on 2014-03-16
Just an observation and perhaps others have experienced this.  
The "Suspend" option puts my system to sleep and it can not be woke up.  I accidentally select it sometimes when shutting down though.

I'm using an HP Compaq Intel Core 2 Duo machine with Ubuntu 12.04 LTS

---

### Post by squakie on 2014-03-17
Many things can affect this. The first place I would look is the swap partition size.  If you are going to hibernate (whether by accident or not ;) ), you basically need you swap partition (or swap file if you have gone that route) to be a little over twice the size of physical memory, at least the last I heard. 

You may also be having problems with video not restarting, perhaps power options not being compatable, etc..

---

