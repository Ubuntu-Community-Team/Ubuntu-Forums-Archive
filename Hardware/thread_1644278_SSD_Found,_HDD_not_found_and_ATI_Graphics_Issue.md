---
title: "SSD Found, HDD not found and ATI Graphics Issue"
date: 2010-12-13
forum: Hardware
---

### Post by akand074 on 2010-12-13
Hey guys, 

I just built a new computer and when I went to install Ubuntu using my 10.10 CD it only finds my SSD as sdb but won't find my 1TB Sata III WD Caviar Black hard drive connected to a Sata III port. Perhaps moving it to a Sata II port might cause it to be found but that defeats the purpose. Anyone know why it's not finding my 1TB? I was trying to install "/" on the SSD and "/home" on my 1TB. I went ahead and installed Ubuntu on just the SSD temporarily to see if it would find my 1TB after the install.

Also after I installed my fglrx proprietary drivers, my system went to "Windows 95 mode". It just has grey ugly looking panels and is in what looks like 1680x1050 mode (I have black bars all around) when I'm catalyst is showing that I'm in 1920x1080. Also if I switch the resolution down, it works fine (takes up the whole screen) Anyone know anything about that issue either? Thanks for the help.

```
andrew@andrew-desktop:~$ sudo fdisk -l

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008d3ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6994    56174592   83  Linux
/dev/sdb2            6994        7298     2438145    5  Extended
/dev/sdb5            6994        7298     2438144   82  Linux swap / Solaris

```

Above as you can tell.. not recognizing my HDD.

---

### Post by cascade9 on 2010-12-13
> **akand074 said:**
> Hey guys, 

I just built a new computer and when I went to install Ubuntu using my 10.10 CD it only finds my SSD as sdb but won't find my 1TB Sata III WD Caviar Black hard drive connected to a Sata III port. Perhaps moving it to a Sata II port might cause it to be found but that defeats the purpose. Anyone know why it's not finding my 1TB? I was trying to install "/" on the SSD and "/home" on my 1TB. I went ahead and installed Ubuntu on just the SSD temporarily to see if it would find my 1TB after the install.

What motherboard? 

I'll bet that you've connected the WD Black to a addon SATAIII chip (normally some 2 port RAID chip). Lots of the addon chips have poor or non-existant linux support. 

Just hook the HDD up to the SATA II ports.....no HDD comes close to using SATAII bandwidth and there is normally virtually no difference in speeds between a SATAIII HDD on SATAII and SATAIII.

---

### Post by akand074 on 2010-12-13
> **cascade9 said:**
> What motherboard? 

I'll bet that you've connected the WD Black to a addon SATAIII chip (normally some 2 port RAID chip). Lots of the addon chips have poor or non-existant linux support. 

Just hook the HDD up to the SATA II ports.....no HDD comes close to using SATAII bandwidth and there is normally virtually no difference in speeds between a SATAIII HDD on SATAII and SATAIII.

I'll probably do that. I have an Asus Sabertooth x58 motherboard. Sata II should work hopefully. This graphics issue is ridiculous though.

---

### Post by akand074 on 2010-12-13
Okay so I put it in sata II.  It recognizes it fine now. Graphics are nuts still. Trying a clean install.

EDIT: Issue persists after a clean install. I'm going to mark this thread as solved in reference to my HDD issue and start a new thread for my graphics problem.

---

### Post by cascade9 on 2010-12-14
> **akand074 said:**
> Okay so I put it in sata II.  It recognizes it fine now. 

Yep, it was the #%&$%& marvel controller stuffing things up. 

Good to hear at least one problems fixed, good luck with the video issues ;)

---

