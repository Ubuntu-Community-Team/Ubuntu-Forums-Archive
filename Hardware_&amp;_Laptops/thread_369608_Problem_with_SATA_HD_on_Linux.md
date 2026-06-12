---
title: "Problem with SATA HD on Linux"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by jerrykenny on 2007-02-24
Heres th e Hard-drive . . . 

Western Digital 250gb Sata II  (wd2500ks)

The drive is partitoned into 30 gb FAT32 partitions.

The drive runs perfectly with windows, and in fact has just passed an extended (24hrs) test using Western Digitals Diagnostic tools on Windows.

But with Debian . . . . . !!!!  I get file corruption, files go awol, fsck goes berserk, dmesg complains vebosely that 

ATA: abnormal status 0x7F on port 0xCC07
  Vendor: ATA       Model: WDC WD2500KS-00M  Rev: 02.0
  Type:   Direct-Access                      ANSI SCSI revision: 05

thats just the start of it usually . . . .


Why does this happen only with linux ?  surely if it was a hardware problem, windows would suffer similarly, ?

?

?

---

### Post by taurus on 2007-02-24
You are not supposed to run fsck on vfat or ntfs!  If you do, you are only asking for trouble.

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by jerrykenny on 2007-02-24
I was as surprised myself when fsck was scrolling itself thru the terminal during the bootup !    thats when I lost a lot of files.

heres fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        1976      514080   82  Linux swap / Solaris
/dev/hda3            1977        4408    19535040   83  Linux
/dev/hda4            4409        4865     3670852+   5  Extended
/dev/hda5            4409        4846     3518203+  83  Linux
/dev/hda6            4847        4865      152586    b  W95 FAT32

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3890    31246393+   c  W95 FAT32 (LBA)
/dev/sda2            3891       30401   212949607+   5  Extended
/dev/sda5            3891        7537    29294496    b  W95 FAT32
/dev/sda6            7538       11184    29294496    b  W95 FAT32
/dev/sda7           11185       14831    29294496    b  W95 FAT32
/dev/sda8           14832       18478    29294496    b  W95 FAT32
/dev/sda9           18479       22125    29294496    c  W95 FAT32 (LBA)
/dev/sda10          22126       25772    29294496    c  W95 FAT32 (LBA)
/dev/sda11          25773       29419    29294496    c  W95 FAT32 (LBA)
/dev/sda12          29420       30401     7887883+   c  W95 FAT32 (LBA)

---

### Post by taurus on 2007-02-24
Did you mount the /dev/sdaX from /etc/fstab?  If you are, can you post it here.

```
cat /etc/fstab
```

---

### Post by jerrykenny on 2007-02-24
yes, here it is

jerryspc:/home/jeremy# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>    <dump>  <pass>

proc            /proc           proc    defaults        0 0

################ 40 GB ol faithfull ###############################

/dev/hda3       /       ext3    noatime,errors=remount-ro 0 1
/dev/hda5       /mnt/backup     ext3    defaults        0 2
/dev/hda6       /mnt/mailbox    vfat    umask=000       0 0
/dev/hda2       none            swap    sw              0 0

##################### Removable Media ###########################

/dev/hdc        /media/cdrom0   udf,iso9660 users,noauto 0 0
/dev/fd0        /media/floppy0  auto    rw,users,noauto  0 0

###################### 250 GB Sata ################################

/dev/sda1       /media/Offis-Docs vfat  rw,umask=000    0 2
/dev/sda5       /media/music    vfat    rw,umask=000    0 2
/dev/sda6       /media/Dads-Films  vfat rw,umask=000    0 2
/dev/sda7       /media/Girls-Films vfat rw,umask=000    0 2
/dev/sda8       /media/photos   vfat    rw,umask=000    0 2

---

### Post by taurus on 2007-02-24
And that is why fsck is running because you have the wrong value in there.  The last value should have been 0 instead of 2 since you don't want Ubuntu to scan your vfat or ntfs.

```

/dev/sda1 /media/Offis-Docs vfat rw,umask=000 0 2
/dev/sda5 /media/music vfat rw,umask=000 0 2
/dev/sda6 /media/Dads-Films vfat rw,umask=000 0 2
/dev/sda7 /media/Girls-Films vfat rw,umask=000 0 2
/dev/sda8 /media/photos vfat rw,umask=000 0 2

```
Therefore, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace the last digit to 0.

---

### Post by jerrykenny on 2007-02-24
O MY GOD   !!!!

has that been the root of all my woes !!!!!


OMG 


OH Dear

---

### Post by jerrykenny on 2007-02-24
OK, just rebooted with new revised fstab . . . 

still get this error

ATA: abnormal status 0x7F on port 0xCC07
  Vendor: ATA       Model: WDC WD2500KS-00M  Rev: 02.0
  Type:   Direct-Access                      ANSI SCSI revision: 05


Will now start up ktorrent and leave running overnight . . . see what happens


Thanks Taurus . . . . 

Will tag this solved (for now anyway)

---

### Post by jerrykenny on 2007-02-24
OK, just rebooted with new revised fstab . . . 

still get this error

ATA: abnormal status 0x7F on port 0xCC07
  Vendor: ATA       Model: WDC WD2500KS-00M  Rev: 02.0
  Type:   Direct-Access                      ANSI SCSI revision: 05


Will now start up ktorrent and leave running overnight . . . see what happens


Thanks Taurus . . . . 

Will tag this solved (for now anyway)

---

### Post by jerrykenny on 2007-02-24
No joy . . . . heres what happens as soon as I start ktorrent

ATA: abnormal status 0xD0 on port 0xD407
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: (BMDMA stat 0x22)
ata1.00: tag 0 cmd 0x35 Emask 0x20 stat 0x40 err 0x0 (host bus error)
ATA: abnormal status 0xD0 on port 0xD407
ATA: abnormal status 0xD0 on port 0xD407
ATA: abnormal status 0xD0 on port 0xD407
ATA: abnormal status 0xD0 on port 0xD407
ATA: abnormal status 0xD0 on port 0xD407


and ktorrent hangs.

---

### Post by taurus on 2007-02-24
Try booting into XP and defrag those partitions again.  Maybe fsck did some funky stuff  to those partitions.  Any reason why you divided that harddrive into a bunch of small chunks?

---

### Post by jerrykenny on 2007-02-25
Yes, I was under the impression that was the maximum size of fat32 partition one could have . . . . . anyway, some of the later partitions might have the "noauto" boot option, or perhaps read-only, plus it will quicker to defrag.

A suggestion from a Gentooist was that the stock kernel might not be fully configured for my setup (probably the controller rather than the hard-drive)

---

### Post by jerrykenny on 2007-02-26
Thanks Taurus, I booted into windows and had windows "clean-up" the drive . . . 

Also removed "system-restore" from that partition, and had the system-restore points removed.  

The above measures recovered space on the partition which was being inexplicably used up . . . . I couldn't see any hidden files which could have accounted for the discrepancy.

Finally defragmented, which took a couple of hours, . . . . . now linux is quite happy, and Ktorrent is whirring away steadily.

The following error message is still present on bootup

**ATA: abnormal status 0x7F on port 0xD407**

It worries me . . . . . also the drive was fairly shakey even before fsck had a go at it . . . . still not convinced it isn't a kernel issue ? . . . . 2.6.17 ran very well, but problems coincided with the change to 2.6.18  also on 2.6.17 I hadnt checked dmesg for error messages, so cant tell if the above error message was there at that time.

            Thanks again    Jerry

---

### Post by jerrykenny on 2007-04-20
Finally !   the hard drive completely borked out.   And immediately the Western-Digital-diagnostics reported that a faulty sata cable was probably to blame,   and it was . . . .!

I would've gotten round to it, but I had just tried swapping to a new sata socket, and was experimenting with various bios permutations (ie legacy sata control)

You'd think a reliable sata cable would be the easiest fri&*ing thing to manufacture ?

Its a bit off topic but I reckon theres much more dodgy unreliable hardware on sale now than there ever has been.

Thanks for your help everyone, and sorry for wasting your time on an essentially hardware problem

---

### Post by ShiningHolden on 2008-03-06
I downloaded the latest Debian net-install disk, but I did not want to install all the packages. I installed XFCE, and then I rebooted, and now I can not get back in. I had this problem before. It is a random problem, but now I can not get in to a shell at all.

Debian came with 2.6.18.8-686.

I am aware that this is not Debian support.
PLEASE help me.

I get tons of "ATA: Abnormal status error 0x7f" errors through my whole kernel boot.
I get "hda: lost interrupt"
I get "hdb: lost interrupt"
I get "hdd: lost interrupt"
I get tons of ACPI PCI errors.

It does not load me to a shell. Sometimes, I get the initramfs spcheel.

I use 3 SATA 3.0gb/s hard drives, and 1 SATA DVD-Burner (I unplugged it to see if it changed anything).

Here is my system:
Gigabyte GA-P35-DQ6 F7d BIOS
Intel Core 2 Quad Q6700 2666MHz @ 3500MHz
2GB Crucial DDR2-1066 5-5-5-15
eVGA 8800GTS G80 640mb

Here are my drives:
Western Digital 150gb Raptor (MBR/Windows XP Professional SP2)
Western Digital 250gb Caviar16? (Linux)
Western Digital 320gb (NTFS storage)

If anyone can tell me how to get half *** in, I can rebuild the latest kernel, or provide reports and debugging back.

Thank you.

---

