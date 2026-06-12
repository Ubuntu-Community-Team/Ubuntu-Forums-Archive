---
title: "&quot;grub boot disk error&quot; after install"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by gregcoit on 2009-03-15
Hi all,

I have an interesting copmuter made by Promise that has 2 IDE slots and a promise SATA card.  The first IDE slot has a 32mb flash drive.

I purchased a 1TB SATA drive to use in the computer.  I decided to install ubuntu server to the SATA drive, and then sometime later put some kind of tiny linux on the 32mb IDE drive for disaster recovery.

The install went fine, but upon reboot, I realize that the bios doesn't have a "boot to sata" option (it does have the following options in the "first boot device" menu.  

LS120
HDD-0
SCSI
CDROM
HDD-1
HDD-2
HDD-3
ZIP100
USB-FDD
USB-ZIP
LAN
DISABLED

So, I booted to a live-cd and inspected the install.  The SATA drive is seen by both the install of ubuntu server and the kubuntu live-cd as /dev/sda and the IDE drive is seen as /dev/sdb.

Using the live-cd, I told grub:
root (hd0,0)
setup (hd1)

(assuming this would install grub onto the mbr of the IDA drive.  And it appears to have done so, because aafter a reboot, I get:

grub boot disk error

I *think* grub is launching on the IDE drive but then is unable to see the SATA drive.

How does one point GRUB on an IDE drive to boot a SATA drive that the bios apparently doesn't see?

Thanks!

Greg

---

### Post by gregcoit on 2009-03-15
I must be getting complacent.  Linux works in so many ways I just assume it will *always* work.

I looked a bit closer at this computer.  It has a Promise FastTrak S150 TX2.

Normally, this can be an issue in linux if one wants to use the built-in raid controller, but that's not my case - i just want it for SATA support.

I'm now thinking that I should replace the 32MB flash card with a ATA hard drive (the box has 2 bays) and install Ubuntu Server on the ATA and us ethe SATA for storage.

Any other solutions that folks can think of?

Greg

---

### Post by meierfra. on 2009-03-15
> Using the live-cd, I told grub:
root (hd0,0)
setup (hd1)

This does not work. "root (hd0,0)" means that grub  will look on   first partition of the boot drive for stage2.  But the boot drive is your IDE drive, while stage 2 is on the sata  drive .
Try this

```
sudo grub
device (hd0) /dev/sdb
device (hd1) /dev/sda
root (hd1,0)
setup (hd0)
quit
```



But if your bios don't detect the sata drive at all, this does not work. 
Then you will either have to find a way for the bios to detect the sata drive, or  create a boot partition on the IDE drive.

---

