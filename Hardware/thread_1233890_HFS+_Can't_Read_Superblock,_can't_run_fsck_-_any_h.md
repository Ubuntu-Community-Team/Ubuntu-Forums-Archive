---
title: "HFS+ Can't Read Superblock, can't run fsck - any hope?"
date: 2009-08-07
forum: Hardware
---

### Post by 0graham0 on 2009-08-07
Hi,

I have an HFS+ IDE drive which became unmountable after attempting to connect it to a Windows 7 machine running MacDrive 8.0.0. I ran a diagnostic test to check if the drive was damaged and it passed the test with no problem. This leaves me guessing there is a filesystem problem?

I have now installed the drive in a machine running Ubuntu 9.04 x64. On boot I see the HFS+ partition listed in the "Places" menu. When I attempt to mount the drive I receive the message:```
Unable to mount the volume 'HFS'. 
Details: mount: /dev/sda3: can't read superblock
```Running sudo dmesg | tail returns ```
[ 1818.387802] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[ 1818.390077] hfs: failed to load root directory
```

I installed hfsprogs and attempted to run fsck.hfsplus which returns:```
sudo fsck.hfsplus /dev/sda3
** /dev/sda3
** Checking HFS Plus volume.
   Invalid node structure
(4, 1613)
   Invalid record count
(4, 1613)
   Catalog file entry not found for extent
(4, 0)
** Volume check failed.
```

Just wondering if anyone has any further ideas/instructions/advice? It would be greatly appreciated.

Thanks,
Graham

---

### Post by macburn on 2011-06-06
Hi,

I have the same problem with Natty (11.04).
Anyone can solve this issue ?

Thanks in advance !

---

### Post by macburn on 2011-06-06
> **macburn said:**
> Hi,

I have the same problem with Natty (11.04).
Anyone can solve this issue ?

Thanks in advance !

Oops !

I am afraid, but I have just solved the problem.
My disk was named /dev/sdb2 instead of /dev/sdb1.
But I don't know why, because I have only one partition...

---

