---
title: "WANTED: Real-time kernal"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by 3l3vans on 2009-03-12
i am running Xubuntu 8.04 and i was wondering how hard it would be to switch to Ubuntu Studio's kernal OR any realtime kernal. i want it for audio applications but i don't want to switch to Ubuntu Studio because i really dig Xubuntu. i found a tutorial using a redhat kernal but was wondering if there was an Ubuntu patch available. any info would help...thanks 


                                3l

---

### Post by damis648 on 2009-03-12
```
sudo apt-get install linux-rt
```
should do the trick. Just reboot and do
```
uname -r
``` to make sure you're running the kernel.
Cheers!

---

### Post by 3l3vans on 2009-03-12
THANK YOU! that did the trick. even easier than i thought it would be! 3l

---

### Post by damis648 on 2009-03-12
> **3l3vans said:**
> THANK YOU! that did the trick. even easier than i thought it would be! 3l

No problem! Cheers. :popcorn:

---

