---
title: "Configuration For Highest Performance"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by Precipitous on 2009-06-11
I am getting ready to install Ubuntu Studio on a new 1TB drive. What is the best configuration? Is it better to put everything on the one drive, or should I use a secondary drive for the swap file? Should the Home directory be on a separate drive? Should I use just one drive, but with different partitions for specific items, etc?

---

### Post by Mighty_Joe on 2009-06-11
My opinion as a professional software developer: "premature optimization is the root of all evil" - Donald Knuth 
Unless you can identify and quantify something that is holding back your system and the gain another configuration will provide, it is pointless to jump through hoops in the pursuit of "performance".  You can't tell if you've improved things and may, in fact, have made things worse.
In my experience, it is faster, easier and cheaper to buy better hardware than it is to tweak your way to better performance.
[IMHO]("http://www.acronymfinder.com/IMHO.html"), [YMMV]("http://www.acronymfinder.com/YMMV.html")

---

### Post by tgalati4 on 2009-06-11
Some things I do for a faster system:

Break in your hard disk.  Run it through badblocks or use Ultimate Boot Disk utilities to exercise the drive.

memcheck your ram for 30 complete (all ten tests) cycles.  Will probably take overnight.  Overclock your RAM if you can--you can typically get a 10% increase in throughput.  Verify speed and reliability with memtest.

Get a fast, smaller hard disk for your boot disk, such as a Western Digital Raptor.  Save the 1 TB for your data files.  Break in your boot drive before installation.

Overclock your CPU if possible by 10-15%.  Install 64-bit, and lots of RAM, 2-4 GB.

Performance gains are worthless if your system locks up due to motherboard errors, so you need to do some burn-in testing to verify both the speed increase and long-term reliability.

---

