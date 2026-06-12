---
title: "Grub Problem"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by weaverdj on 2009-07-29
Performed a normal update manager today 7/29.  Required a restart and now I get this message:

GRUB loading stage 1.5.

GRUB loading, please wait 
Error 18

Then it just hangs.  No other os installed, no other hardware/sorftware changes.  Worked fine before updates.

Celeron 2.0 Gh
1 gig of ram

Ubuntu 9.04

---

### Post by merlinus on 2009-07-29
Post results of

```
sudo fdisk -l
```

---

### Post by weaverdj on 2009-08-05
I can only boot from the live cd.  will that command show what you want from that type of boot?

---

### Post by realzippy on 2009-08-05
There is a SuperGrubDisc,pretty small,a LiveCD
which can repair broken GRUBs easily..

[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

---

### Post by weaverdj on 2009-08-08
Tried every option w/supergrubdisk.  No go.  Have searched forums and tried every suggestion - reinstall grub, etc.  Nothing.  HELP!!

---

### Post by merlinus on 2009-08-08
Whilst running from the live cd, open a terminal and post results of

```
sudo fdisk -l
```

---

### Post by weaverdj on 2009-08-08
Sorry, here it is.

Ubuntu 9.04 is actually at /dev/sda8.  How do I boot from there?

255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ba8ed00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         135     1084356   83  Linux
/dev/sda2             136        7297    57528765    5  Extended
/dev/sda5            6995        7297     2433816   82  Linux swap / Solaris
/dev/sda6             136         261     1012032   83  Linux
/dev/sda7            6709        6994     2297263+  82  Linux swap / Solaris
/dev/sda8             262        6439    49624753+  83  Linux
/dev/sda9            6440        6708     2160711   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fa02811

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux

---

### Post by merlinus on 2009-08-08
Which partition is linux root?  Also, on sda you have 3 swap partitions, and the partition numbering is incorrect.

---

### Post by Flapse on 2009-08-08
Okay, so I've got the same problem, only I (for some reason) installed grub in Windows... How do I make it go away?! (From the windows prompt).
I've tried the commands like, Bootfix, fdisk, CFGboot or whatever...
What should I really use? (I'm using windows 7 btw)

---

### Post by merlinus on 2009-08-08
Try booting from windows cd, choose recovery, then /fixmbr and/or /fixboot.

---

### Post by Flapse on 2009-08-09
Yeah..no it's exactly those commands I've tried.
It says those commands are not external nor internal. What should I do? 
Remember that this is the WINDOWS prompt. So that might be why they're not working? I don't know...Please help :p

---

### Post by weaverdj on 2009-08-09
I started an install off the live cd for Ubuntu 9.04 just to see the partition information.  I began with this disk and a clean install then a couple of upgrades since then 8.XX to 9.4, etc.  It looks like the current version 9.04 is installed on /dev/sda8.

As for the swap partitions and incorrect numbering, I just don't know.

---

