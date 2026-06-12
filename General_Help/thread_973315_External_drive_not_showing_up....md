---
title: "External drive not showing up..."
date: 2008-11-06
forum: General Help
---

### Post by x C0MMAND0 x on 2008-11-06
So I have a new eSATA external drive, and if I turn it on, and then boot up my computer, it shows up and I can access it just fine.  However, if it is NOT turned on when I boot up, the device does not show up after I turn it on once I'm already logged in and everything.  

How do I get it to show up?  I checked the bios and everything seems to look okay, but I'm not sure if that is the problem.

---

### Post by taurus on 2008-11-06
I would turn on the drive, plug it to your machine, and look at the log file to see if the kernel even detects it.

Applications -> Accessories -> Terminal
```
dmesg | tail
```

---

### Post by x C0MMAND0 x on 2008-11-07
The output before and after turning the device on and connecting it were the same, so I would say that it is not even being detected.  

Does this have something to do with eSATA?  Because if I connect it with USB 2 after booting up, the device does show up...

---

### Post by x C0MMAND0 x on 2008-11-11
Bump?  Anyone?

---

### Post by x C0MMAND0 x on 2008-11-14
I think I found the problem.  I am not sure if my motherboard supports hot-swappable SATA drives.  My motherboard name is [A8AE-LE]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00496280").  I can not tell if it is hot swappable, does anybody know how to find this out?

---

