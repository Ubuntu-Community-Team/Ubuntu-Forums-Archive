---
title: "Installing XP (Ubuntu already installed)"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by Photosynthesis on 2009-05-16
Hi, I have Ubuntu already installed, and I want to dual boot it with XP, but after a while it just gives me a message saying that a problem has been detected and windows has been shut down to prevent damage to the computer.

Any help would be appreciated (: Thanks

---

### Post by pastalavista on 2009-05-16
> **Photosynthesis said:**
> Hi, I have Ubuntu already installed, and I want to dual boot it with XP, but after a while it just gives me a message saying that a problem has been detected and windows has been shut down to prevent damage to the computer.

Any help would be appreciated (: Thanks

The problem is probably you have no space on the drive to install Windows. You'll need to boot the Ubuntu live CD and run gparted  (partition Editor)in order to shrink the Ubuntu partition and make room to add an NTFS partition for Windows. After you install Windows, you'll have to boot from the Ubuntu disk again to setup grub or you won't be able to boot Ubuntu.

---

### Post by Photosynthesis on 2009-05-17
> **pastalavista said:**
> The problem is probably you have no space on the drive to install Windows. You'll need to boot the Ubuntu live CD and run gparted  (partition Editor)in order to shrink the Ubuntu partition and make room to add an NTFS partition for Windows. After you install Windows, you'll have to boot from the Ubuntu disk again to setup grub or you won't be able to boot Ubuntu.
Yeah I used gparted to shrink the Ubuntu partition, then I put the XP install disk in, but it came up with the error message. Do I have to do something specific with the second (non Ubuntu) partition after I have it?

---

### Post by pastalavista on 2009-05-17
> **Photosynthesis said:**
> Yeah I used gparted to shrink the Ubuntu partition, then I put the XP install disk in, but it came up with the error message. Do I have to do something specific with the second (non Ubuntu) partition after I have it?
yes, you need to make a Windows partition. Format the empty space as NTFS or Fat32. The XP disk should be able to see it. I think it didn't see the unformatted space because it didn't recognize the formatted part. Windows is much more stupid than Ubuntu... well, not stupid, just proprietary... snobbish, haha

---

### Post by Photosynthesis on 2009-05-17
Ok, so I tried formatting the empty space as NTFS and Fat32, but each one gave me the same error message when I had the XP disks in.

---

### Post by pastalavista on 2009-05-17
Ah well, that can only mean that your XP disk is an OEM 'recovery' disk designed to work with a hidden partition on the hard drive that must have gotten erased when you installed Ubuntu. If you could find a regular Windows disk, it would probably work. You can download Windows 7 for free still.

---

