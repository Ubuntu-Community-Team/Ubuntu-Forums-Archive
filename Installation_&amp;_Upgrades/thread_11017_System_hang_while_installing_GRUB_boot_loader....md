---
title: "System hang while installing GRUB boot loader..."
date: 2005-01-13
forum: Installation &amp; Upgrades
---

### Post by YSHP on 2005-01-13
Hi everyone,
           This is my pc rig:
1.  Asus P4P800SE
2.  P4 1.6A northwood
3.  Radeon 9200 VIVO
4.  KVR 512mb PC2300
5.  Maxtor 80gb 7200rpm IDE HDD
6.  WD 120gb SATA HDD
7.  Creative SB Live DE 5.1
8.  TDK CD-RW
9.  LG CD-ROM

Ok, the problem is that im running everything are smooth and fast, but when it comes to install the GRUB boot loader, it hang and 50% insallation, don't tell me that only i cant wait for the long installation, i took 3 hours and the screen still indicate 50% left installation...What should i do so that i can install my ubuntu? Thank you very much!!

---

### Post by rider343 on 2005-01-13
hoary or warthy?

---

### Post by ktulu1115 on 2005-01-13
I have the same problem.  System install goes smoothly until installing grub.

My system specs:

AMD Athlon64 3200+
ASUS A7N8X Deluxe
Corsair XMS PC3200 1024mb RAM
Adaptec AHA-2940U2W SCSI Controller

I'm using Warty for AMD64 install ISO.

Running "grub-install (hd0)" is all I see with the progress meter at 50%.  The system is not hung, I can go to another virtual terminal, kill the process and try again, but the same thing ends up happening.

/var/log/messages (and virtual terminal 3) has only these lines at the end:
Unpacking grub (from .../grub_0.95+cvs20040624-3ubuntu17_amd64.dev) ...
Setting up grub (0.95+cvs20040624-3ubuntu17) ...

Last line I see on virtual terminal 4 is:
Jan 13 10:09:32 (none) user.notice grub-installer: info: Running chroot /target/sbin/grub-install --no-floppy "(hd0)"

Why is it using a CVS version of grub???  Or am I reading this incorrectly?

I've upgraded from Fedora Core 3 64-bit, although the partitions were formatted so no existing data should be there (except for /home).  I also have an IDE 200gb disk (only ATA device in the system, set up as one large XFS partition) that's used just for storage, I wonder if grub is getting confused and installing to the wrong MBR.  Not sure if it's smart enough to install on sda instead of hda (I boot from SCSI, like I said the ATA disk is for storage only).  I recall during FC3 (and FC2) installs I had to manually tell the installer to install on /dev/sda instead of /dev/hda.

Any ideas?  I've heard wonderful things about Ubuntu and I'd hate to turn it down just cause of this simple problem.  Thank you.

---

### Post by ktulu1115 on 2005-01-13
Cause was what I originally guessed - grub install was getting confused onto which drive to install (or something along those lines).  I temporarily disconnected my ATA drive and reinstalled, then it worked perfectly.

YSHP: Not sure of your partitioning scheme but if you can I'd try removing one of the drives just for the install, and it should work fine then.

Seems like there is a bug on grub install when a system has multiple drive interfaces - SCSI/ATA, SATA/ATA, etc.  IIRC, Linux can emulate SATA devices as SCSI ones (esp since some newer SATA drives support SCSI features - TCQ, etc).

Where can I submit this bug report?

---

### Post by YSHP on 2005-01-13
what is hoary and warthy?

yes, i tried to unplug my ATA harddisk, it works smoothly till the GRUB installation, but when i plug them both together, i found out that when it comes to scanning the CD-ROM will run very very slow like 3hours for 70%. Can anyone tell me what can i try? thank you...

Btw, im using the EXT3 file system to install ubuntu...what can i do to make the GRUB installation finish? coz i cant use both HDD to install ubuntu, it will make the installation slow even te scaning files from the CD will kill me...

---

### Post by uiteoi on 2007-03-06
I have the same problem: Installing GRUB hangs at 50% mark using Ubuntu 6.06 i386, alternate.

I have 4 ATA drives part of a non-trivial RAID 5 and LVM configuration. I therefore cannot remove more than one ATA drive without breaking the RAID 5 array.

The message window (F4) displays:
grub-installer: info: Installing grub on '(hd0)'
grub-installer: info: grub-install supports --no-floppy
grub-installer: info: Running chroot /target /sbin/grub-install --no-floppy "(hd0)"
grub-installer: info: Probing devices to guess BIOS drives. This may take a long time
kernel : [17191573.796000] Driver 'sd' needs updating - please use bus_type methods

# cat /proc/mdstat
...
md0 : active raid5 hde1[0] hdi1[0] hdg1[0]

# mount
...
/dev/md/0 on /target/boot type ext3 (rw,data=ordered)
...


Please help.

---

### Post by uiteoi on 2007-03-06
My problem was that RAID5 is not compatible with GRUB.

So I changed the /boot partition to RAID1 and was then able to install GRUB without any problem.

I now have a fully functional Ubuntu 6.06 booting on my RAID array.

---

### Post by schuettr on 2007-08-12
I had a similar problem - trying to install Ubuntu server to a Raid 5 array. Initially, I configured 3 MD's - / (root), swap, and /home. I got repeated failures of the GRUB installation. 

After reading the message, above, I then configured 4 MD's - /BOOT, / (root), swap and /HOME and everything went great. the /BOOT partition was set up as RAID1.

This was all done on UBUNTU 7.04

---

