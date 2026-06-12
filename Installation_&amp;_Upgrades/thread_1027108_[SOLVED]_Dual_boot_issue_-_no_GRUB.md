---
title: "[SOLVED] Dual boot issue - no GRUB?"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by Smeags on 2008-12-31
Ok, so I already had Vista installed on one hard drive.  I installed Ubuntu on a second drive.  After the installation, my system rebooted and immediately booted straight into Vista.  What happened to GRUB?

I did some searching and found a possible solution for restoring GRUB.  Did this:

Booted LiveCD, opened terminal and did: sudo grub.  Then I did: find /boot/grub/stage1.  It returns: (hd0,0).  So I did: root (hd0,0).  Then did: setup (hd0).  Finally: quit.

Rebooted and my system boots straight into Vista again, no other options.  I was going to use EasyBCD to add an Ubuntu boot option to the Vista boot loader, but I can't even do that without having access to /boot/grub/menu.lst so I can use the Ubuntu boot information to configure NeoGrub correctly.

Any suggestions?  Let me know if there's any other information you need.

---

### Post by Herman on 2008-12-31
Try Booting LiveCD, open terminal and do: sudo grub.
 Then do: find /boot/grub/stage1
setup (hd1) 
 quit

I think there's some confusion about which hard disk is number1, I'm guessing GRUB's stage1 is probably getting installed in your second hard disk's MBR, probably your GRUB thinks that's (hd0). So by installing it to (hd1), you should be able to outsmart it.

Regards, Herman :)

---

### Post by Smeags on 2008-12-31
Quick question based on your response, Herman.  I think I understand what you're saying.

I actually have 3 drives in my system.  When installing Ubuntu, Ubuntu recognized the (formerly) empty (Ubuntu) drive as sda, my storage (NTFS) drive as sdb, and my Vista drive as sdc.

Would sda correspond to hd0, sdb correspond to hd1, and sdc correspond to hd2?  If so, would I want GRUB to be on hd0 (as it currently is) or hd2 (the Vista drive)?

---

### Post by Bucky Ball on 2008-12-31
The grub menu is not by any chance hidden? Sounds weird but I had that problem when I installed once. It was set to hide the menu by default! Went to /boot/grub/menu.lst and stuck a hash in front of:

# hiddenmenu

I think it is. Long-shot but ya never know ...

[quote=Smeags]Would sda correspond to hd0, sdb correspond to hd1, and sdc correspond to hd2? If so, would I want GRUB to be on hd0 (as it currently is) or hd2 (the Vista drive)?[/quote]

... and yea, that is right. Windoze likes to be sda1, though, and as Herman says, the confusion is probably to do with looking in the wrong place at boot. Fixable once you have identified what is actually happening.

---

### Post by 2hot6ft2 on 2008-12-31
> **Smeags said:**
> Quick question based on your response, Herman.  I think I understand what you're saying.

I actually have 3 drives in my system.  When installing Ubuntu, Ubuntu recognized the (formerly) empty (Ubuntu) drive as sda, my storage (NTFS) drive as sdb, and my Vista drive as sdc.

Would sda correspond to hd0, sdb correspond to hd1, and sdc correspond to hd2?  If so, would I want GRUB to be on hd0 (as it currently is) or hd2 (the Vista drive)?
That should be correct. hd2

---

### Post by 2hot6ft2 on 2008-12-31
How about posting the output of:
```
sudo fdisk -l
```

---

### Post by Herman on 2008-12-31
:D Just install it to all three MBRs then, it won't hurt anything. :D

---

### Post by 2hot6ft2 on 2008-12-31
> **Herman said:**
> :D Just install it to all three MBRs then, it won't hurt anything. :D
LMAO.....that would work too. Never have to try and find it then.

---

### Post by Smeags on 2008-12-31
> **2hot6ft2 said:**
> How about posting the output of:
```
sudo fdisk -l
```

Here it is:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e6e2cda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5727    46002096   83  Linux
/dev/sda2            5728       12450    54002497+   5  Extended
/dev/sda5            5728       11952    50002281   83  Linux
/dev/sda6           11953       12450     4000153+  82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1cf01cf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9039    72605736    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea013

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19581   157284351    7  HPFS/NTFS
/dev/sdc2           19582       39162   157284382+   7  HPFS/NTFS
```

---

### Post by Smeags on 2009-01-01
Ok, so I decided to just go ahead and try using: setup (hd2) in GRUB to see if that would work and it didn't.  I got an Error Code 15 on boot.  I searched for some solutions, but it looked like it was going to require some work and I don't feel like it, nor do I have the time.

So I deleted the partitions on the Ubuntu drive and overwrote GRUB with Vista's boot loader again, so I'm back to square one.  The only difference is that I had to switch the SATA ports of the hard drives around a little before Windows would recognize my Vista install in order to reload its boot loader.

So now my Vista install is sda (hd0), storage is still sdb (hd1) and my empty Ubuntu drive is sdc (hd2).  Question: what can I do the next time I install Ubuntu to make sure that GRUB is on the correct disk or partition?  Where should GRUB be located?  Is there anything I need to make sure I do during Ubuntu install to get things running correctly?

By the way, this is for 8.10 Intrepid just in case it matters.

---

### Post by ranfow on 2009-01-01
I think you should install grub by default, it will be installed in hd0, and it will add Vista to boot menu automatically.
ps:may be you can try adding ubuntu to Vista boot menu.

Regards, ranfow

---

### Post by Herman on 2009-01-01
> Question: what can I do the next time I install Ubuntu to make sure that GRUB is on the correct disk or partition? Where should GRUB be located? Is there anything I need to make sure I do during Ubuntu install to get things running correctly?Well, you didn't do anything wrong, but there has always been a problem with computer's BIOSes and GRUB trying to guess which hard drive the BIOS will use as the first one.

As you know, the BIOS always tries to boot the MBR of whichever hard disk it has listed first in it's hard disk boot order. GRUB needs to install it's stage1 to the MBR of whichever hard disk the BIOS thinks is the first hard disk. Unfortunately, it isn't simple for GRUB to understand the BIOS information on that for some reason, especiailly if there's a mixture of different kinds of disks in the computer, like some IDE and some SATA drives.
Some BIOSehave a habit of listing SATA drives first, others IDE. Fortunately most computers agree on the idea of listing USB drive last.

Apart from that, hard drive order also depends on IDE drive jumper settings, and sometimes even the chronological order of when they were plugged in and detected by the BIOS. (If you plug a SATA cable into the second or third slot and boot, then plug a new SATA drive into the number 1 hole, the one that was plugged in first might stay as number 1 hard drive, even though it's plugged into the second port. Until something happens like you reset your BIOS or something. 

The easiest and quickest way to overcome that kind of problem is to go into your BIOS settings and change the hard disk boot priority. 
If Ubuntu doesn't boot next time you install, you have a 50% chance you'll be able to guess which of the other two hard disks should be set as number1 in the BIOS.
Then you should at least be able to boot into GRUB, and see if the other operating systems all boot okay. If not, you just need to switch the other two hard disks in the BIOS boot order. (set which will be second and third hard disk).

If you do it that way, you won't need to edit any files, or re-install GRUB.

Regards, Herman :D

---

### Post by Irony on 2009-01-01
Does the output of sudo fdisk -l match that shown in gparted, i.e. do the partition ids and partition numbers match?

If not then you need to relabel fdisk.

Also what is the grub menu.lst in sda1?

---

### Post by Smeags on 2009-01-04
Sorry I was gone for a few days for New Year's.  Thanks for the responses.  I'm thinking that if I do things the same way I did them last time (now that I have changed my hard drives around) it should work properly, since my Vista disk is now sda (hd0).

I'll give it another shot when I get some time and I'll let you guys know if I run into any issues.

---

### Post by Smeags on 2009-01-05
Update: I got things working now.  I tried it a little bit differently this time around.  I ended up installing the boot loader to the same partition that I installed Ubuntu on.  Then when I rebooted, my system booted directly into Vista.  Then from Vista I used EasyBCD to add Ubuntu to the Vista boot loader and viola!  I should have done it that way the first time.

Thanks for all the help/suggestions!  I'm sure I'll be asking many more questions now that I can get into Ubuntu, but so far has been good.  I've got video drivers and compiz running.  I've got sound with my X-Fi, and that's all I've been able to mess around with so far.

---

### Post by Bucky Ball on 2009-01-05
Nice work! You got there in the end. Keep asking questions and good luck.  :)

---

