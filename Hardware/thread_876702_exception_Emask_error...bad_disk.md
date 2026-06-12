---
title: "exception Emask error...bad disk?"
date: 2008-08-01
forum: Hardware
---

### Post by Innova on 2008-08-01
A friend gave me a lap top that no longer boots into xp, it blue screens on startup.  I put in the ubuntu live cd, and hooked up a usb drive.  When it was booting up, the following errors were displayed:

ata1.00:  status:  { DRDY ERR }
ata1.00:  error: { UNC }
ata1.00:  exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00:  BMDMA stat 0x4
ata1.00:  cmd c8/00:80:48:26:7e/00:00:00:00:00/e3 tag 0 dma 65536

It repeats this message several times, along with the following one:

Buffer I/O error on device sda1, logical block xxxxxxx

The live cd did boot after several of these messages.  I was able to create a disk image based on this link:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I'm assuming the hard drive is gone, but before I order a new one for my friend, I was wondering if someone could confirm this?

Thanks in advance.

---

### Post by Innova on 2008-08-01
I also ran "badblocks" (didn't even know there was such a program).  It reported 
 
badblocks:  Input/output error during test data write, block 1356288 (got this for some other blocks too).

badblocks then just hung with the last few lines looking like this:

1356349
1356350
1356351
badblocks:


No more output, but the command line didn't return.

---

