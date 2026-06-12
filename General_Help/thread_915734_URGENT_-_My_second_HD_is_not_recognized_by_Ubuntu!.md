---
title: "URGENT - My second HD is not recognized by Ubuntu!!"
date: 2008-09-10
forum: General Help
---

### Post by maxmanapple on 2008-09-10
My second HDD is no longer recognizable by Ubuntu and can't mount at all. What can I do to mount it again?

Please answer as fast as possible, important data inside! Any help appreciated!

---

### Post by triphazard on 2008-09-10
I'd start by doing a sudo fdisk -l (lower case L) and see if it's listed there.  Not sure if you've done that yet.  If it is you should be able to at least check the disk...if not then it could be a loose cable or maybe worse.

---

### Post by maxmanapple on 2008-09-10
It's listed, but the partition I want doesn't appear:

```
 sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20409532416 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6020

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2372    19053058+  83  Linux
/dev/sda2            2373        2481      875542+   5  Extended
/dev/sda3            2482        2482           0    e  W95 FAT16 (LBA)
/dev/sda5            2373        2481      875511   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
240 heads, 63 sectors/track, 10587 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x493a4d2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10587    80037688+   c  W95 FAT32 (LBA)

```

It should appear, at Disk /dev/sdb, a partition, sdb2, which was an NTFS partition for main data and about 75 GB of size. This partition (/dev/sdb1/) it used to be a Windows XP instalation partition of 5 GB of size. but now it's empty.

---

### Post by forger on 2008-09-10
> **maxmanapple said:**
> My second HDD is **no longer** recognizable by Ubuntu and can't mount at all. What can I do to mount it again?

So this means it was recognizable before..? What were you actually doing before it got "lost"?:confused:

---

### Post by maxmanapple on 2008-09-10
Trying to install Windows 98. But the drive that got "lost" was unplugged for safety reasons. If anything should happen it would be with Disk 1 (Ubuntu disk). Now I plugged it again and ran Ubuntu, and "poof", the partition's missing!

---

### Post by maxmanapple on 2008-09-10
Please, I need my data back! I'm asking you, DO SOMETHING! IT'S IMPORTANT DATA IN RISK!!!!

---

### Post by lintoolman on 2008-09-10
Does the computer's bios see the drive?  

If it doesn't ensure the data and power cables are securely connected. 

I understand you have three hard drives, the two listed by fdisk and one missing drive.

---

### Post by maxmanapple on 2008-09-10
The BIOS does see the drive.

---

### Post by lintoolman on 2008-09-10
Have you tried booting a live cd to see if all three drives are recognized?

---

### Post by maxmanapple on 2008-09-10
Yes, I tried and it still didn't recognize the drive.

---

### Post by mixmaster on 2008-09-10
From the fdisk listing, the whole of the second disk is now a Windows Fat disk.  At a guess I would suggest that you unplugged the wrong disk when you were playing with your win98 installation and managed to trash it.  Try unplugging the same cable as you did last time and then boot the system.  If nothing (or win98 ) comes up then I am probably right.  If the win98 install repartitioned the disk without actually writing anything you might be able to restore the original partitions and recover the disk.

Good luck.

PS:
When you are posting please remember that the people helping you here are generally unpayed enthusiasts trying to help fellow users.  Remarks like "Please, I need my data back! I'm asking you, DO SOMETHING! IT'S IMPORTANT DATA IN RISK!!!! " are really not appropriate.

---

### Post by maxmanapple on 2008-09-10
> **mixmaster said:**
>  If nothing (or win98 ) comes up then I am probably right. 

It wasn't a sucessful install, it blocked out right from the beginning.
When I unplugged the boot disk and rebooted, at the DOS screen, it appeared the following:
```

Erro MBR

Prima uma tecla
```

(MBR error - Press a key)

When the key was pressed it appeared:
```
DISK BOOT FAILIURE. PLEASE INSERT BOOT DISK AND PRESS ENTER TO CONTINUE
```



> **mixmaster said:**
> If the win98 install repartitioned the disk without actually writing anything you might be able to restore the original partitions and recover the disk.


Now, the thing is: How do I do it? How do I recover my partitions back?

---

### Post by mixmaster on 2008-09-10
If you unplugged the same disk as last time and now get this message, then you definitely unplugged the wrong disk for safety when attempting the install, otherwise you would still boot linux.

It sounds as though the mbr on the second drive has been damaged or overwritten.  In theory it is possible to rewrite the mbr with the same partition information and recover the contents.  However, this is not trivial and if the failed win98 installation actually started to write files it probably won't help.

If your data is genuinely valuable then I would recommend a professional data recovery service, but that won't come cheap.  If losing the data is just an inconvenience you could try googling "restoring mbr" - that gave me a long list of sites with hints, software and options.  Which ones you should try really depends critically on exactly what you did before the failure.  Bear in mind that if you do go the self-help route you could make things even more difficult for a professional restorer at a later date.

I'm sorry I can't give you more explicit instructions. I've been in the trashed disk situation before and had some success recovering things but I'm not an expert and the rescue usually involved thrashing around for longer than it would have taken to rebuild the system from scratch.

It is too late now, but a cardinal rule of data management is that valuable data should be kept in at least two completely separate places. An external HD, an old PC or a dedicated LAN storage box are all ideal for reasonably secure backup although if it is really important you should burn it to a CD/DVD and take it to a different physical location (in case of fire).

---

### Post by forger on 2008-09-10
Hm.. what kind of hard drive? There might be a chance you mixed the cables (?)
Check the sockets/pins/needles at the back of the hard drive - any of them bent sideways?

I would switch all the cables (power and data) of the ubuntu disk with the second hard drive.

---

