---
title: "Ubuntu Studio + Vista + RAID 0 !!! :o"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by Regele IONESCU on 2009-03-14
Hello everybody!
This my first post on Ubuntu forums. Have tried a little time to play with CentOS and now I am trying to switch to Ubuntu Studio as I see lots of features needed for a multimedia artist as I am.

The problem is that I had a bad, really bad, bitterly bad experience trying to install CentOS beside Vista(lost 500 GB of vital information - though I am still alive).

I know that Linux+Vista+RAIDdrives is a killing combination. But I saw some posts and I have hope that it is possible to make this dangerous cocktail work. And as an artist I could not live with simple combination.

My configuration is based on an Intel D975XBX2 mainboard, with Vista installed on a two SATA RAID 0 configuration and a non-RAID SATA drive.

I wish I would install Ubuntu Studio on the non RAID drive and keep both Vista and Ubuntu. Is that possible?(Without reinstalling Vista nor losing again 500GB of information) and how could I do it?

God help us all!
Honestly,
Regele IONESCU

---

### Post by logos34 on 2009-03-14
It should be possible without major difficulty (although with raid there's always an element of uncertainty).  The trick is to make sure the grub boot loader is installed to the ubuntu disk (the non-raid sata), not the mbr on the raid volume.  At step 7 ("ready to install" screen) press 'Advanced' and replace the default location '(hd0)' with the '/dev/sdc' or whatever the ubuntu drive is.  Then toggle the Bios boot order when you want to start linux instead of windows/vista.  Either that or add ubuntu to the vista boot menu with [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Linux").

---

### Post by Regele IONESCU on 2009-03-14
I have installed UbuntuStudio following the EasyBCD guidelines. I put grub on sdc5 and added a new entry into EasyBCD by selecting the Ubuntu Root partition(the one where grub is installed onto).

Ubuntu won't boot: I get a screen with
"BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Loading new partition
Bootsector from C.H. Hochstatter
Cannot load from harddisk.
Insert Systemdisk and press any key"

What can I do? The so called "liveCD" is the one I installed UbuntuStudio from?

Many thanks!

God help us all!
Honestly,
Regele IONESCU

---

### Post by logos34 on 2009-03-14
{lease post your 

**sudo fdisk -l**

ok, so ubuntu / is sdc5

In the meantime you could try this:

boot the live cd and reinstall Grub to the MBR of the ubuntu disk, according to the instructions on the link in my signature below.  For instance, if the 'find' command returns '(hd2,4)', then you want to do 'setup (hd2)'.  Now change the Bios hard disk boot priority to boot the non-raid sata disk with ubuntu first.  Hopefully that will get you into linux.

---

### Post by Regele IONESCU on 2009-03-14
I did all the steps from "How to install grub" and now I get the same error message ("BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Loading new partition
Bootsector from C.H. Hochstatter
Cannot load from harddisk.
Insert Systemdisk and press any key")

and if I press a key it says:

GRUB Loading stage1.5.
GRUB loading, lease wait...
Error 21

Find command returned me (hd2,4). In the last steps should I use (hd2,4) instead of (hd0)???

---

### Post by Regele IONESCU on 2009-03-14
Here is my fdisk -k as I copy it by hand:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units=cylinders of 16065*512=8225280 bytes

Device      Boot Start  End      Blocks        Id     System
/dev/sda1        1      15666    125829120      7     HPFS/NTFS
/dev/sda2        15666  47536    256000000      7     HPFS/NTFS
/dev/sda3     *  47536  121602   594936832      7     HPFS/NTFS


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units=cylinders of 16065*512=8225280 bytes


Disk /dev/sdb doesn't conatin a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units=cylinders of 16065*512=8225280 bytes


Device    Boot  Start End   Blocks     Id    System
/dev/sdc1  *    1     31330 251656192   7    HPFS/NTFS
/dev/sdc2       31331 46995 125829112+  7    HPFS/NTFS
/dev/sdc3       46996 60801 110896695   5    Extended
/dev/sdc5       46996 60234 106342236   83   Linux
/dev/sdc6       60235 60801   4554396   82   Linux swap / Solaris

---

### Post by logos34 on 2009-03-15
> **Regele IONESCU said:**
> 
Find command returned me (hd2,4). In the last steps should I use (hd2,4) instead of (hd0)???

no, you already installed it there.  You want it on the mbr so you can boot that disk directly.

Maybe the problem is you need to use Lilo instead of grub for Bootpart:
> [How to add Linux]("http://www.winimage.com/bootpart.htm")

For Linux, you must install Lilo at the beginning of the Linux partition (as is the case with the OS/2 boot manager) and then add the Linux partition with BootPart:

---

### Post by Regele IONESCU on 2009-03-15
I am using Ubuntu Studio. Is Lilo an available option at installtion(I have not seen one could chose between Grub and Lilo) or should I get it from somewhere else?

I found a post saying that running Linux on a SATA drive with multiple system partitions is not possible, i.e. Linux system should be lonely on that SATA drive.

Another aspect is that I installed Linux on the last partitions of the drive, not at the beginning of it. Might this be a problem?

Sorry for my stupid questions. I am a beginner. Thank you very much for your help.

God help us all!
Honestly,
Regele IONESCU

---

### Post by logos34 on 2009-03-15
linux works fine on sata's with other OSs.  Position of linux / partition on the disk doesn't matter (only time it does is on older machines where the Bios can only see as far as the cylinders at the beginning of the drive).

Not sure why you're getting that Bootpart error message, and the grub error, if you installed grub stage1 on the MBR of sdc, and that is the disk you're booting directly.

You could try using Super Grub Disk to boot linux partition (see link in my signature).  Try that and post back.  At least we'll know ubuntu studio is working and maybe you can replace Bootpart on sdc with the regular windows bootloader (what is on sdc1? is that a bootable XP partition or what?)

---

