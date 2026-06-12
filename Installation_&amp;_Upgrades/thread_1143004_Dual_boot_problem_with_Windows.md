---
title: "Dual boot problem with Windows"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by bernimoses on 2009-04-29
I have already read many topics and how-tows but nothing can help me.

My problem:
I have 1 harddisk with 3 partitions.

fdisk:
```
Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x80d2f3ee

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               2       29226   234749812+   f  W95 Erw. (LBA)
/dev/sda2           29227       30400     9430155   83  Linux
/dev/sda3   *       30401       30401        8032+  82  Linux Swap / Solaris
/dev/sda5               2       29226   234749781    7  HPFS/NTFS

```on sda5 is Windows XP but the Windows bootfile were on sda2 (ntfs). sd3 was free space. I don't know were sda1 there was. That was my old configuration.

I chose sda2 for ubuntu because i want to have windows as 2nd system. before the installation i copied the boot things (boot.ini, bootfont.bin, ntdetect.com and ntldr) to sda5 my old windows partition. then i installed ubuntu with no problems. in the grub configuration the windows system was detectet and configured.
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title        Windows XP
rootnoverify    (hd0,4)
savedefault
makeactive
chainloader    +1
```but that didn't worked because the standard boot partion was the old sda2 (ntfs). I have tested several configurations with grub but nothing worked.

can anyone help me? i'm confused.

sry for my bad english and thank you for the fast help. :)

---

### Post by Mark Phelps on 2009-04-30
GRUB counts the drives sequentially, not by the "sda" number, so in your case, the XP boot files would be on the fourth partition -- "3" in GRUB terms.  Try changing to (hd0,3) and see if that works.

---

### Post by bernimoses on 2009-04-30
i've tried all partions (0-5) and nothing worked.

---

### Post by Mark Phelps on 2009-04-30
> **bernimoses said:**
> i've tried all partions (0-5) and nothing worked.

"nothing worked" doesn't help us much since we can't see the system.

What exactly happens when you change the rootnoverify statement?

---

### Post by bernimoses on 2009-04-30
oh sry. there was always the same error: "error 12 invalid device requested".

---

### Post by Herman on 2009-04-30
> error 12 invalid device requestedYou are being given that error message because you are trying to use the 'makeactive' command in GRUB on a logical partition and GRUB can only set a boot flag in a primary partition.

In some computers, Windows seems to need the boot flag before it will boot.
The 'makeactive' command is supposed to make sure the 'boot flag' is set on the Windows partition you are trying to boot. The 'makeactive' command is only needed if you have more than one Windows installed in the same hard disk. 

You can set a boot flag in your Windows partition with a partition editing program such as GParted or any other partition editor. The boot flag can just remain there, Linux doesn't need the boot flag, so it will probably never need to be moved again. That means you can do without the 'makeactive' command in GRUB now.
When you remove the 'makeactive' command, you should be able to boot Windows XP from GRUB.

```
title        Windows XP
rootnoverify    (hd0,4)
savedefault
chainloader    +1
```

---

### Post by bernimoses on 2009-05-01
ok i set the boot flag to sda5
```
Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x80d2f3ee

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               2       29226   234749812+   f  W95 Erw. (LBA)
/dev/sda2           29227       30400     9430155   83  Linux
/dev/sda3           30401       30401        8032+  82  Linux Swap / Solaris
/dev/sda5   *           2       29226   234749781    7  HPFS/NTFS

```and changed the menu.lst to
```
title        Windows XP
rootnoverify    (hd0,4)
savedefault
chainloader    +1
```but yet it says:
```
Starting up...
a disk error occurred
please press str+alt+entf to restart...
```while i set the boot flag i see that sda5 is in the partitiontree under sda1
[[IMG]http://img3.imagebanana.com/img/729aww4w/Bildschirmfoto.png[/IMG]]("http://img3.imagebanana.com/")
is that a problem?

---

### Post by Herman on 2009-05-01
[A Disk Read Error Occured]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Disk_Read_Error_Occured") - that's an error message from the boot sector, so at least you're hitting the right boot sector now I think.

You might need to use a [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and run: FIXBOOT
That might fix your Windows XP boot sector. I hope! :)
It wouldn't hurt to run CHKDSK /F or CHKDSK /R if you have time. You have a yellow warning triangle in front of your Windows partition, meaning it's ready a file system check. A file system check may possibly fix your problems. 

/dev/sda5 has to be in the partition tree under /dev/sda1 because /dev/sda5 is a logical partition and /dev/sda5 is the 'extended' partition. That's not normal for a Windows installation, but we should be able to get it to boot up and run just as well. 
It is your problem exactly, but we should be able to get your Windows to boot again regardless.

---

### Post by bernimoses on 2009-05-01
sry that didn't worked. i run fixboot and chkdsk bbut there is always the same error.

---

### Post by Herman on 2009-05-01
Okay, I have two different ideas about what to try next.

One idea is to go to the following website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm").  From that website if you read under the heading 'Make a NTLDR boot disk to get back into Windows', you will find in step2, some download links where you can download an .iso file to burn to a CD, or a floppy disk .exe file or a USB .zip file.
Those files, when made into a CD or a floppy disc or USB, contian the three vital Windows XP boot loader files, NTLDR, NTdetect.com and a special generic version of boot.ini.
That means it can boot your Windows XP even if something's wrong with the MBR, the boot sector, or any of those three files. In other words, if your Windows is bootable at all, that CD, USB or floppy should boot it. 
Maybe we should try that and then once it's booted, work back from there to see if we can actually fix the problem.

My second idea is one that doesn't make very much sense, but it worked for me once before with a similar problem. Use a Parted Magic Live CD or GParted Live CD or Gnome Partition Editor in a recent version of Ubuntu Live CD to shrink the Windows XP partition from the left-hand side (start), towards half way.
I don't know how much data you have in there, but if you haven't made a backup of it yet, you should do so before using any partition editing program.
It would be even better if you can copy the data to some other hard disk and double-check to make sure it's copied and verify the copies are good before deleting it from the Windows XP partition. You may need an external USB hard drive or some other hard drive if you have very much data to move. 
The shrink the partition away from the start of the hard disk.
When the boot sector is moved to somewhere further away from the start of the hard disk, try again to boot it, and see if that helps or not.

That worked for me once for a freind's Windows XP when nothing else worked, but I don't know why. I moved his XP from one end of the hard disk to the other and it booted right up! We installed Ubuntu in the first half of the same hard disk and Ubuntu worked fine there, so I don't know if there was anything wrong with the hard disk or not. Once I got XP working, and Ubuntu was installed too, my friend got me to delete Windows XP for him, (after all that work, LOL!). He still has Ubuntu working in that same hard disk without any problems.

If you can shrink your Windows XP partition to less than half, and you shrink the extended partition too, you might even be able to copy and past it to the start of your hard disk again. It will be allocated as partition number 1, and be a primary partition and you will have more of a normal Windows installation then. Maybe that will simplify things, although we should be able to get it to boot as a logical. I have done it myself before and I know it will work, but maybe there is more than one problem.

---

### Post by meierfra. on 2009-05-01
The "starting up" error is usually caused by a wrong "hidden sector" number in the boot sector. "Fixboot"  sometimes corrects that error but not always. So I recommend to fix the starting up error with  testdisk.

Just follow this tutorial:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)


In Step 1:  Use /dev/sda5 

In Step 3:  Use partition(3)


Skip Step 4. Your windows item in menu.lst is already correct.

You need to carry out Step 5.

---

### Post by bernimoses on 2009-05-02
@Herman
> One idea is to go to the following website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm").I tested it and it worked with partition 3 (6 entry in the boot.ini).

because i haven't a backup of my data, i didn't tried your second idea. 

@meierfra.
your tutorial worked great. i made the steps and it worked. step 1 and step 5 i had already made so i have just to do the other steps. but from how you know that it was partition 3? :)

---

### Post by meierfra. on 2009-05-02
> but from how you know that it was partition 3?

From the output of "fdisk":

```
/dev/sda1               2       29226   234749812+   f  W95 Erw. (LBA)
/dev/sda2           29227       30400     9430155   83  Linux
/dev/sda3           30401       30401        8032+  82  Linux Swap / Solaris
/dev/sda5   *           2       29226   234749781    7  HPFS/NTFS
```

Windows is /dev/sda5.  Windows counts  the partitions in the same order as Ubuntu. But it does not count extended partitions (/dev/sda1) and it only counts partitions which really exists (so /dev/sda4 does not count). This leaves

sda2, sda3,sda5

So Windows is the third partition.

> step 1 and step 5 i had already made 
How did you know to do step 5?

---

### Post by bernimoses on 2009-05-02
Herman posted a link to the "[grub page]("http://users.bigpond.net.au/hermanzone/p15.htm#Starting%20up%20.%20.%20.")" and there under the menu point **"Starting up . . ."** was the tutorial.[B]

Oh, and thank you two for the help. :)
[/B]

---

