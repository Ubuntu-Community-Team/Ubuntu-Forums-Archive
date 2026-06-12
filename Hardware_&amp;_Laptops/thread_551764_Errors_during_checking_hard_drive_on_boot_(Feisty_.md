---
title: "Errors during checking hard drive on boot (Feisty Fawn i686)"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by 3doff on 2007-09-15
When starting my Feisty Fawn, it checks mounted drives and the device /dev/hdc1 shows errors on about two screens like this:
> 
[117.166029] Buffer I/O eror on device hdc1, logical block 21436888
[120.745243] Buffer I/O eror on device hdc1, logical block 21436889
...
and so on as I've already said about two screens


Checked this hard drive fully in Windows 2k3 with it's standard hard disk checking utility (with errors correcting mode) - it didn't find any error. The problem remains. S.M.A.R.T. is also ok.


Then I did like here:
[http://ubuntuforums.org/showthread.php?t=366454](http://ubuntuforums.org/showthread.php?t=366454)

> gksudo gedit /etc/default/rcS

there FSCKFIX=Yes
rebooted two times. The problem remains.

Now I've just disabled the disk check on boot like it is written here:
[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

and have found an old topic about like mine problem?
[http://ubuntuforums.org/showthread.php?t=138731](http://ubuntuforums.org/showthread.php?t=138731)

So. System:
AMD Sempron 3000+ 64
EPoX 8KDA7I

I have 2 hard disks.
The problem is on the first and the old one. It is Seagate Barracuda 40Gb ATAIV - IDE w2k3 is installed on it with FAT32 filesystem. One partition on it (FAT32).

The second is also Seagate Barracuda but 250Gb SATA. One partition is NTFS and the others are swap and Ubuntu 7.04 root partitions.

About 9 month's ago Ubuntu 6.06 was instead of 7.04 and everything was ok with hard drives and mounting.
Then there was a power failure on a nearby electric power station and my power module in PC was burnt down. I disconnected all hardware. Than after 6 month bought new power module assembled all old hardware together with new power module. IDE cable or IDE slot was found damaged: secondary slot is used by hard drive and if I connect another cable with CD-RW Nec-NR7900A to primary IDE slot the PC buzzes on BIOS checking connected drives.
So I connected CD-RW to the cable with hard drive (secondary IDE slot).

my /etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=092d2a0d-e1ec-4340-bdda-3bc58262fb51 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
UUID=3F52-1BFF  /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       [COLOR="Red"]0[/COLOR]
# /dev/sda5
UUID=D468CDC9C2D02D76 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=5ccd02bc-da15-4df3-9ae6-88f97900f3ad none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


Hard disk works fine. Only this startup errors on every boot.
Right now I've disabled fsck on /dev/hdc1 and everything is just fine.

sorry for my poor english+)) hello from Russia+)
(Russian community was unable to help me: [http://forum.ubuntu.ru/index.php?topic=12862.0](http://forum.ubuntu.ru/index.php?topic=12862.0))

Thank you for your attention.

---

### Post by 3doff on 2007-09-16
ok than. it's not a problem any more +)
I disabled hard disk check and that's all.

---

