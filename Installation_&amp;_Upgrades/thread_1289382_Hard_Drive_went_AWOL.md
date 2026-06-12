---
title: "Hard Drive went AWOL"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by uppercrustie on 2009-10-12
Hi all,

I am looking for some advice on how to solve some problems caused by a failed installation of Ubuntu 9.10 Karmic Koala.

This is how it went: 
I have 2 hard disks, both SATA, first 250gb the other 160gb. I keep the first for my stable OS and work stuff (nicely separate /Home partition for easy recovery) and use the other to play and try out other distros and new releases. Hard Disk 1 runs Ubuntu 8.10 as Jaundiced Jackalope was playing videos very badly (maybe due to my sis 671 card) and so after much faffing with it I decided to go back to Ibex. 
____________________________________________________

Anyway, so today I tried to install Karmic on my second Hard Disk and my silly machine decided to freeze right on 95% of the installation process. After a hard reboot and a second failed installation I decided to give up. Problem is now my second hard drive is invisible to Ubuntu. BIOS can see it but Ubuntu cannot. Even running gparted from a live CD seems to be unable to see it. I tried fdisk -l with this output:

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091583

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        3039    24410736   83  Linux
/dev/sde2            3040       30401   219785265    5  Extended
/dev/sde5           29849       30401     4441972+  82  Linux swap / Solaris
/dev/sde6            3040       29848   215343229+  83  Linux

Partition table entries are not in disk order

so even here no /dev/sdb...

Any suggestions?

---

### Post by rippin on 2009-10-12
> **uppercrustie said:**
> Hi all,

I am looking for some advice on how to solve some problems caused by a failed installation of Ubuntu 9.10 Karmic Koala.
<snip>
Anyway, so today I tried to install Karmic on my second Hard Disk and my silly machine decided to freeze right on 95% of the installation process. After a hard reboot and a second failed installation I decided to give up. Problem is now my second hard drive is invisible to Ubuntu. BIOS can see it but Ubuntu cannot. Even running gparted from a live CD seems to be unable to see it. I tried fdisk -l with this output:

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091583

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        3039    24410736   83  Linux
/dev/sde2            3040       30401   219785265    5  Extended
/dev/sde5           29849       30401     4441972+  82  Linux swap / Solaris
/dev/sde6            3040       29848   215343229+  83  Linux

Partition table entries are not in disk order

so even here no /dev/sdb...

Any suggestions?

It may be that your LiveCD boot, or fdisk, in use[COLOR=Black]* does not **recognize the file system (ext4?)*[/COLOR]. Try the Ubuntu 9.10 Karmic Koala disk, format the drive and initialize it using FS ext3 and see if life is good again.

---

### Post by uppercrustie on 2009-10-13
> **rippin said:**
> It may be that your LiveCD boot, or fdisk, in use[COLOR=Black]* does not **recognize the file system (ext4?)*[/COLOR]. Try the Ubuntu 9.10 Karmic Koala disk, format the drive and initialize it using FS ext3 and see if life is good again.

yup, tried that.. Unfortunately the Koala is blind to my hard disk too...

---

### Post by Bartender on 2009-10-13
I'm wondering why your PC froze.  Overheating?  Power supply failing?  Does it do this often?

Perhaps downloading and burning to disc the hard drive manufacturer's utility application might work?  Create the bootable disc, and tell it to write 0's to the entire drive.  This takes HOURS, but I imagine the utility is written to ignore previous formatting and just start writing so it may not care if the disc has weird errors.

---

### Post by presence1960 on 2009-10-13
> **uppercrustie said:**
> Hi all,

I am looking for some advice on how to solve some problems caused by a failed installation of Ubuntu 9.10 Karmic Koala.

This is how it went: 
I have 2 hard disks, both SATA, first 250gb the other 160gb. I keep the first for my stable OS and work stuff (nicely separate /Home partition for easy recovery) and use the other to play and try out other distros and new releases. Hard Disk 1 runs Ubuntu 8.10 as Jaundiced Jackalope was playing videos very badly (maybe due to my sis 671 card) and so after much faffing with it I decided to go back to Ibex. 
____________________________________________________

Anyway, so today I tried to install Karmic on my second Hard Disk and my silly machine decided to freeze right on 95% of the installation process. After a hard reboot and a second failed installation I decided to give up. Problem is now my second hard drive is invisible to Ubuntu. BIOS can see it but Ubuntu cannot. Even running gparted from a live CD seems to be unable to see it. I tried fdisk -l with this output:

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091583

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        3039    24410736   83  Linux
/dev/sde2            3040       30401   219785265    5  Extended
/dev/sde5           29849       30401     4441972+  82  Linux swap / Solaris
/dev/sde6            3040       29848   215343229+  83  Linux

Partition table entries are not in disk order

so even here no /dev/sdb...

Any suggestions?

sounds like a hard disk problem. bartender has the right idea. Go to the hard disk manufacturer's site and download their utility that they provide. I know Seagate has a great one called Seatools. Use the one that you can make a bootable CD/DVD from- don't use the version which runs from within windows.

---

### Post by uppercrustie on 2009-10-13
> **Bartender said:**
> I'm wondering why your PC froze.  Overheating?  Power supply failing?  Does it do this often?

Perhaps downloading and burning to disc the hard drive manufacturer's utility application might work?  Create the bootable disc, and tell it to write 0's to the entire drive.  This takes HOURS, but I imagine the utility is written to ignore previous formatting and just start writing so it may not care if the disc has weird errors.

Ok, LL try this.. Yup computer used to freeze quite often. Apparently it was a buggy BIOS, which I have now updated from Packard Bell website. I will see how it all pans out in the near future. Thank you all for your help, I'll let you know how it goes.

P.

---

### Post by uppercrustie on 2009-10-29
> **Bartender said:**
> Perhaps downloading and burning to disc the hard drive manufacturer's utility application might work?  Create the bootable disc, and tell it to write 0's to the entire drive.  This takes HOURS, but I imagine the utility is written to ignore previous formatting and just start writing so it may not care if the disc has weird errors.

Brilliant! Tried that and it solved all my problems.. sure I had to ZERO the drive, but luckily it's only the one I use to experiment. Thank you all for the support.

Pietro

---

