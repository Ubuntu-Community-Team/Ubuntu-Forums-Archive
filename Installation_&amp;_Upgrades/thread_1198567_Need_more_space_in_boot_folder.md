---
title: "Need more space in boot folder"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by Humanities Major on 2009-06-27
Hi, my laptop is currently running on 8.04 and I want to (finally) upgrade to 8.10.  I tried to upgrade but the thingy tell me I need 11 mbs more space in my boot file and to run sudo apt- get clean in the terminal.
I did that but it cleaned away nothing and I can't exactly go deleting things in the boot folder or the computer will just not run.  I have plenty of free disk space so I'm wondering how I can make the boot folder bigger.  Does that make any sense?
Is there another way to install the upgrade without losing all my settings?

---

### Post by raymondh on 2009-06-27
> **Humanities Major said:**
> Hi, my laptop is currently running on 8.04 and I want to (finally) upgrade to 8.10.  I tried to upgrade but the thingy tell me I need 11 mbs more space in my boot file and to run sudo apt- get clean in the terminal.
I did that but it cleaned away nothing and I can't exactly go deleting things in the boot folder or the computer will just not run.  I have plenty of free disk space so I'm wondering how I can make the boot folder bigger.  Does that make any sense?
Is there another way to install the upgrade without losing all my settings?


kindly post output of (from terminal)

```
df -h
```

also of

sudo fdisk -l  

(small L not 1)

also, see links

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

