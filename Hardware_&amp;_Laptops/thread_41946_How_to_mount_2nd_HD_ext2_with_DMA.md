---
title: "How to mount 2nd HD ext2 with DMA"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by Holdem on 2005-06-15
I have a dual boot with XP and a 2nd hard drive which is formated to Ext2. I have mounted it following instructions for FAT mounting on [http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat) . When I copy data it takes an age, how do I know if DMA is enabled?

FSTAB=

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext2    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/xp  vfat    umask=000       0       0

/dev/hdb2       /media/data  ext2    umask=000     0       0

---

### Post by GTvulse on 2005-06-15
Edit /etc/hdparm.conf and add:

```

/dev/hdb {
    dma = on
}

```

DMA will be active after the next reboot. To do it manually, type ```
sudo hdparm -d1 /dev/hdb
``` in a terminal/console. BTW, you may want to do the same thing for your DVD/CD drives. The Ubuntu kernels have DMA disabled by default for all IDE devices except hard disks. I consider this policy a packaging bug although it is is the safest choice (a CD reader/writer with bad DMA handling can and will bork your computer).

---

### Post by Uta on 2005-06-17
I need advice also on how to get my new 2nd hard drive mounted. I see in my laptop's BIOS that the 2nd HD in the modular bay is seen. Once Kubuntu booted, if I run gparted how shall I partition this 40GIG, second HD that will be used only for storage and sharing?
options:Primary Partition or Extented? Filesystem: ext2, ext3...FAT32 etc...? I will be sharing this drive with Mac OS. Please advise and THANKS in advance!

---

### Post by GTvulse on 2005-06-17
Well.. You won't have anything useful until you craete the partitions, format them and mount them, be it at boot by setting the right commands in fstab, or with the help of the automounter.

Now, on the issue of filesystems, I haven't used MacOSX myself, but it is my understanding that it uses UFS1 (as used in FreeBSD 5.2 and older) or HFS+. The 2.6.x linux kernels have full support for HFS+ and read-only support for UFS1 so HFS+ is the natural choice, unless you would share the HD with MS Windows. In that case, FAT32 would be proper.
 
On partitions, that's a matter of taste and need. You can't have more than 4 partitions in a disk with an msdos superblock label, but you can have more in a disk with a BSD label (where they are called slices). An extended partition is defined in the superblock of one of those 4 partitions (in a disk with a BSD superblock label, the partitions are created within a slice, that is, you create extended partitions inside a primary partition). I mention the BSD superblock labels, because MacOSX is based on a BSD variant (FreeBSD) and therefore it most probaly uses disks partitioned with BSD labels.

Personally I use a poorman's data replication schema, say, in a 40Gb disk, I leave at least 10 Gb in a partition I never mount unless I need to make a back up of data in the other(s) partition(s). You may want to use LVM2 instead (but that will make the partitons incompatible with MacOSX).

---

### Post by Uta on 2005-06-18
Thank you for the information. My additional question is: In QTParted or GParted, I don't have the option of writing a HFS+ file system only FAT32, so in theory if I wrote 20 gigs ext3 (only linux could use, see and share this partition) and 20 gigs in FAT32 MacOS, MS and Linux  could use this partition...is that right? Thanks!
PS I was able to make one primary/ext3 and get it mounted but I am guessing MacOS would never be able to read/write or share it with that file system?

---

### Post by GTvulse on 2005-06-18
[QUOTE=Uta]Thank you for the information. My additional question is: In QTParted or GParted, I don't have the option of writing a HFS+ file system only FAT32, so in theory if I wrote 20 gigs ext3 (only linux could use, see and share this partition) and 20 gigs in FAT32 MacOS, MS and Linux  could use this partition...is that right? Thanks!
[/quote]

You can create a raw partition with G/QtParted and format it from MacOSX as HFS+. You are correct that only Linux will be able to read and write to the EXT3 partition  but there are tools to read the contents at least for Win32 systems, namely lstools and a couple of filesystem drivers for the WinNT kernel. And yes, FAT32 can be read and written by all three OSs. BTW, you will need some user space tools, available in Base but not in the CD that you can install with S/Kynaptic, hfsplus and hfsutils.

[quote=Uta]
PS I was able to make one primary/ext3 and get it mounted but I am guessing MacOS would never be able to read/write or share it with that file system?[/QUOTE]

Yes, that's my understanding as well.

---

