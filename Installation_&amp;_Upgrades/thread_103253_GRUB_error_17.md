---
title: "GRUB error 17"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by twshelton on 2005-12-13
I noticed a lot of errors related to the above without much success in resolving.  I just wasted the last 2 hours trying to figure this out only to realize the problem was that I stuck a memory card from my camera into a USB slot.  Then went about my business and rebooted later on.  

The problem is that my GRUB loader is on an external USB drive and now my camera card was also being search for a bootable sector.

Simple resolution ... I removed the memory card.

Just thought I would throw this out there for any others that may have done the same.

Thomas

---

### Post by JoshHendo on 2005-12-13
[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html) :)

> 
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB


I got a error 25 once and the solution was that I installed ubuntu on a slave hdd (stupid me :P)

---

