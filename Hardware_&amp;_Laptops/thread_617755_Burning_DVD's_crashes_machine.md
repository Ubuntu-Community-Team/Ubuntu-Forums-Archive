---
title: "Burning DVD's crashes machine"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by wiz561 on 2007-11-19
Hi!

I posted part of the problem in the 'general help', but now that I've narrowed it down, I thought I would come here.  

I just got a new DVD burner today and just popped it in.  It seemed to erase dvd's fine, but if I tried to burn something, the computer would just turn off.  Tried it a number of times with growisofs and nero, but the same problems occurred.  

I then unhooked it from the IDE interface and plugged in a USB -> IDE adapter I have.  I tried to use growisofs to burn an ISO to the DVD, and it seems to be working better.  (Crossing fingers).  It's 40% done whereas before, it wouldn't even get to 1% before the computer turned off.

I don't know if it's a irq conflict, or if it's a problem with the dvd mount point.  It seems with the USB, it mounted it as /dev/scd0 whereas before, when plugged into the IDE chain, it mounted it as /dev/hda.  

Thanks in advanced for any help!!

Mike

---

