---
title: "Feisty broke my hdd? It works on XP"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by FrostDust on 2007-04-25
I have two hard drives setup as one 28 GB FAT32 drive under JBOD, and it no longer works under Ubuntu. On 6.10, I could use the drive, but there were problems reading/writing large files from it. Now that I've upgraded to 7.04, the drive is mountable, but none of files are visible, and I can't write to it. If I boot the system to Windows XP Pro, I can use the drive perfectly. Is this a known problem with Feisty, or do I just need to download something to fix this?

---

### Post by aberry5555 on 2007-04-25
There are a couple of things about this

a) FAT32 only supports up to 4GB file sizes, which might be why you had problems

b) you may not have mounted it yet

try typing in 

```
sudo fdisk -l
```

and post it back here, see if you can see the FAT32 partition somewhere on your disk.

<--edit-->

Also, go to a terminal and type in 

```
 gedit /etc/fstab 
```

and post back the results of that (fstab is the file that dictates what hard-drives are mounted at start-up and where they are)

---

### Post by FrostDust on 2007-04-25
Oddly, while the drive (it was mounted normally as hde1) is listed in fstab, it doesn't even show on the partition editor anymore.

Results of fdisk -l:
```
Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          13      104391   83  Linux
/dev/hda2              14        2563    20482875   83  Linux
/dev/hda3   *        2564        4670    16924477+   7  HPFS/NTFS
/dev/hda4            4671        4863     1550272+  82  Linux swap / Solaris

Disk /dev/hdb: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3739    30033486   83  Linux
/dev/hdb2            3740        3740           0    e  W95 FAT16 (LBA)

```

Contents of fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=a3b54992-612c-4c39-9637-27d544345eb7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=74cf29a0-e029-4edd-a570-7c4fa961f45c /boot           ext3    defaults        0       2
# /dev/hdb1
UUID=47f3cb2d-daa4-4660-8ee8-515ecc37cc06 /home           ext3    defaults        0       2
# /dev/hde1
UUID=461A-D096  /mnt/hde1       vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=0aefbb7c-d2de-4548-bfff-41f2b81a7a6c none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by aberry5555 on 2007-04-25
Is it not the second partition on the second disk? If not then it's strange, as it means linux isn't reading your partition table properly.

---

### Post by FrostDust on 2007-04-25
My hard drives are as follows:

I have a 40GB drive with partition 1 being /boot, partition 2 being Ubuntu, 3 being WinXP Pro, and 4 being Linux swap.

I then have a 30 gig drive which is Ubuntu's /home.
All of the above work just as expected.

In addition, I have a 20 gig and 8 gig drive, set up as JBOD, through a RAID card. This makes them appear as one ~28 gig, FAT32 drive to the OS. Under Windows, it works perfectly. On 6.10, I could write and read to it, but it seems that moving/writing a large amount of data at once forced it to become unmounted. As of 7.04, I can't mount it, and the drive doesn't even show up in GParted. I glanced at the Hardware Information program, and while the RAID card shows up, the drives attached to it don't.

Is there some command I could use have the system recreate fstab, or otherwise recognize the drive once again? Would I have to resort to downgrading my system to 6.10, even?

Also, that second partition on the second disk is an anomoly as well; it doesn't show up in GParted. I haven't bothered mounting it to see if it works or not.

---

### Post by aberry5555 on 2007-04-26
it sounds like your RAID card is either not configured properly or it has the wrong drivers... try re-loading the driver with a new one from the manufacturer's site, the modprobe it. Otherwise I'm a bit stumped on that one, RAID isn't really my forte, post back what you find anyway in case I think of something though

Good Luck!

---

### Post by FrostDust on 2007-04-26
I think I found the correct drivers here: [http://www.iteusa.com/software_download/software_download2.asp#IT8212 ATA133 Controller]("http://www.iteusa.com/software_download/software_download2.asp#IT8212 ATA133 Controller"), but it says I have to compile the driver into my kernal. That sounds a bit over my head; is there a guide somewhere on how to do this?

---

### Post by ronmonki on 2007-04-28
Hi , 

there is a guide how to do this for the one of the older kernels, I should imagine it would be fairly similar if you search for posts including my name ronmonki, u will find a post detailing the steps for a previous kernel.

I never wrote the tutorial but I posted a comment on it.

Cheers

---

