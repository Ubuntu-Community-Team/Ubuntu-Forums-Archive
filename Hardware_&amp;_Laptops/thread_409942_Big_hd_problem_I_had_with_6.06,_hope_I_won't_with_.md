---
title: "Big hd problem I had with 6.06, hope I won't with 6.10"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by dentament on 2007-04-15
Hi, some months ago I had a bad experience with ubuntu 6.06 installed on a western digital hard-disk (on via vt8235 chipset). At every boot I got the following warning msg in dmesg:

```
VP_IDE: IDE controller at PCI slot 0000:00:11.1
**** SET: Misaligned resource pointer: dfeea0c2 Type 07 Len 0
```

... but my drive mounted correctly most times. Only sometimes it did not, and these times dmesg showed a "DriveReady SeekComplete Error" about my hd. I did not investigate that much. At first fsck massive data corruption was detected. Most personal sensible data was recovered (and I did backup that on another drive), but I lost some stuff and system data and decided to reinstall 6.06 (after having checked my drive with wd diagnostics, which showed no problems, I reinstalled repartitioning and all, and without recovering my data from the backup drive because I just wanted to test). After reinstalling I hacked a bit with kernel parameters but with no result and same beahaviour ("Misaligned" etc. at every boot, sometimes no mount and "DriveReady SeekComplete Error"); then at first fsck, same data corruption. Then I reinstalled ubuntu 5.10, which always worked no problem before and has worked no problem until now (it's about 2 years I think). Now, since 5.10 is going to be unsupported, I'm trying 6.10 ... its livecd gives no warning in dmesg (while 6.06's livecd does give the "misaligned" ecc. msg), so I'm installing it just now and I hope (I think) it's not going to make mess. I think the problem with my hd on 6.06 could be related with some bug in how it's kernel version manages the via chipset, but couldn't find much about this searching around. Does anyone know more about this issue?
Bye.

---

### Post by Chappy7777 on 2007-04-15
No,

But since I had issues w/6.10 and had to remove it in order to reinstall 6.06, please let us know how you made out. 

Thnx, Chappy

---

### Post by dentament on 2007-04-15
> **Chappy7777 said:**
> No,
But since I had issues w/6.10 and had to remove it in order to reinstall 6.06, please let us know how you made out. 
Thnx, Chappy

er, what kind of issues?
anyway no problems until now, I rebooted lot of times today and never had strange messages in dmesg, while with 6.06 I always had the "misaligned" etc. one

---

