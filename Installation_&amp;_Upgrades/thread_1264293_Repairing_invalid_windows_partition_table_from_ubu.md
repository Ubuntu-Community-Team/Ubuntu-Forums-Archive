---
title: "Repairing invalid windows partition table from ubuntu"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by jkmuller on 2009-09-12
Hi all,

I was attempting to rework the partitions on my laptop and was trying to redo the Windows MBR when I made a mistake. I was using ms-sys and entered a command something like "sudo ms-sys -m /dev/sda1" where I should have entered "sudo ms-sys -m /dev/sda"

What I did, apparently, was screw up my Windows partition table. That's the error message I receive when I try to start my computer. I believe all my data should be there, so my question is can I do anything to 1) fix the partition table from Ubuntu, or 2) somehow recover my data before reinstalling?

Thanks!

---

### Post by jerrrys on 2009-09-12
this may work

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

