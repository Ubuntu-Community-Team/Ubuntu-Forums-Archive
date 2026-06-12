---
title: "External USB Hard disk not mounting in Ubuntu 7.10"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by Mohamed Fahim on 2008-02-27
Hi all,
  I am using dual booting with winxp pro and ubuntu 7.10. I also have 160 gb internal hard disk and 120 gb external hard disk now my problem is at first i tried to install in my external hard disk but in middle of the instalation of Ubuntu in it stopped then i installed in another partition of my internal hard disk now my problem is when i go into ubuntu its not showing up the external hard disk at all i tried lsusb sometimes it shows profilic technology (i.e. my external hard disk) after sometime it dissappear s now my question is how to make it work can somebody help thanks in advance.

:confused:

---

### Post by Rocket2DMn on 2008-02-27
Can you please plug in the drive and post the output of these commands:
```
sudo fdisk -l
dmesg
```

---

