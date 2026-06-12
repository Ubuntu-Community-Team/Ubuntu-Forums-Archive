---
title: "[SOLVED] Install fails i/o error"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by beachdaze on 2009-01-07
OK - when trying to install 8.10 from CD the install fails at roughly 58% every time.  I have downloaded the iso multiple times, burned to 3 differnt brand of CDs, using 3 different burners.  With any of the disks I will receive multiple "can't read from disc/file size doesn't match" type messages on different files.  I have tried different install drives as well.  All burned discs pass the check from the boot menu and ram passes the test as well.

I have tried safe graphics mode, apic and lapic off etc..  No changes.  I know I've had issues with CentOS and LVM so I made sure that the install was not setting up any LVM.  The target drive is listed as sdc (300GB sata).  sda is a 1TB for storage, and sdb is the Windoze drive.

Thinking it may be a bad cluster on the HDD, I manually set the partitions with varying size/configurations (i.e. move the swap to start of the drive then to the end of the drive) to see if it would fail at a different point.  But still fails at 58% of the copy.

I have used this drive and CD to install on this same machine before without any problems.  Live CD functions fine.  The whole reason for this is to get a MythTV system up and running.

Here is the component list:

MoBo:  Asus A8N-SLI Deluxe
CPU: AMD 6x x2 3800+
RAM:  4GB (4x1GB DDR 400)
Video:  Nvidia GeForce 6600GT 256MB
Sound: Creative X-Fi Platinum
SDA:  1TB Seagate Sata
SDB: Maxtor 300GB Sata (Windoze)
SDC: Maxtor 300GB Sata (troublemaker)

Any help please?  Not sure where to go next.

Thanks -Bruce

---

### Post by Pumalite on 2009-01-07
Have you tried the amd64 Alternate CD?

---

### Post by beachdaze on 2009-01-07
> **Pumalite said:**
> Have you tried the amd64 Alternate CD?

Downloading it now.  Will update afterwards.

---

### Post by beachdaze on 2009-01-07
Ran the install using the AMD64 cd.  Still received file copy errors, but it looks like it finished the install.  It never asked where to install grub, so I can't boot to the drive.  All that boots is the sdb/Windoze OS.

I'm at a loss as to why this is happening.  On a lark, I downloaded and used the Mythbuntu 8.10 AMD 64 disk.  No copy errors, but again no option as to where to install grub, so no boot.

Will try again after I get something to eat (and a good stiff drink to boot)

Bruce

---

### Post by Pumalite on 2009-01-07
I don't know about Mythtv, but a Live CD; at step 7 provides accessing 'Advanced Tab', where you can determine where to install Grub.
Here is a guide:
[https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD](https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD)

---

### Post by beachdaze on 2009-01-07
Think the boot issue is do to a mistaken boot order.  For what ever reason the newer 1TB drive, which is attached to the third sata port, shows as sda, the drive attached to the first sata port is sdb (Windoze) and the drive attached to the second sata port is sdc (my target drive).  When I went to the advanced tab I chose hd0, but looking back that may be the sda drive.  So I'm thinking I need to install grub on hd1?  I tried to reinstall again to make a different choice, but the i/o error has returned again.

Putting it aside for the night and will try again tomorrow when I have a more level head.

Thanks for the help Pumalite.

Bruce

---

### Post by beachdaze on 2009-01-08
Issue is not solved, but I got 8.10 to install this morning.  I still have issues with GRUB, but will move to a new thread.

---

