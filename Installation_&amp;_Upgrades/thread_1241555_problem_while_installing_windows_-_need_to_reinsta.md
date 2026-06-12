---
title: "problem while installing windows - need to reinstall GRUB"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by sandy8925 on 2009-08-16
Ok here's my problem. I had Ubuntu 9.04 running well on my fujitsu C1321 laptop. I needed to install Windows XP on it. The partitions were like:

47 MB - empty partition. planning to install GRUB here
1 GB - linux swap
Approx. 40 GB - ext4 - Ubuntu 9.04 clean install with GRUB on same partition
Approx. 39 GB - NTFS (created by previous XP install) - having some data which has been backed up

I backed up whatever I needed from my last partition and booted the Windows XP install cd provided by Fujitsu along with the laptop. It listed the above drives in the same order with following names : 

E:
F:
G:  (unknown) has jaunty on it
C: (ntfs)

I wanted to install in C but it said it was unrecognizable or whatever so I deleted that partition (yes I'm sure of that) and then tried to create a new NTFS partition. It gave out yet another error message which said that it couldn't create any more partitions since the maximum numebr of partitions had already been created. I'm guessing that it was talking about primary partitions so if I created a secondary partition and created a new 39 GB partition under that it would have worked. Either way I just put off the laptop (without pressing the F3 key for exiting). On restarting (I had removed the CD) it didn't boot Ubuntu. The following error message was displayed:

Error loading operating system

My guess is that the Windows setup has happily modified the boot records or something like that or might even have damaged the partition table. I was thinking of using USB creator to get the Ubuntu Live CD on a USB pendrive but I forgot to do so. I have another comp (my dekstop).So is there any way of installing grub on my laptop without having to download the entire ubuntu iso file ? My laptop can boot from pendrive and CD. Remember I've used ext4 for my Ubuntu partition and /boot is also on the  same partition. I have iso's of OpenSUSE 11.1 and Fedora 10 (i think).

Thanks for reading the really long post !

---

### Post by Partyboi2 on 2009-08-16
Hi, you could give [[COLOR=Blue]super grub[/COLOR]]("http://www.supergrubdisk.org/") ago, a lot smaller then downloading the Ubuntu iso.

---

### Post by presence1960 on 2009-08-16
Boot from the Ubuntu live CD, choose "try Ubuntu without any changes". When the desktop loads open firefox & come back here. Download the Boot Info Script from my signature line to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted here highlight all text and click the # sign on the toolbar to place code tags around the text.

This info will give us a clear look at your setup and boot process.

BTW linux doesn't use the terminology of C;, D:, E:, etc to designate disks and partitions. the first disk is sda, the first partition on the first disk is sda1, the second partition on the first disk is sda2, etc. The second disk is sdb. The first partition on the second disk is sdb1, the second partition on second disk is sdb2, etc. It will make things a lot easier & avoid confusion if you use those terms rather than C:, D:, E: which have no meaning in linux. You will get better help that way.

---

### Post by sandy8925 on 2009-08-17
Yeah I knew about the /dev/sda thing.I just mentioned it as C:,D:,E: etc. since I forgot which was which and I wanted to show in what order it was listed in the Windows setup.

BTW I've booted using the Ubuntu 8.10 Live CD. Looks like it can't read ext4.  I have Fedora 10 live cd though and I've read that it can read ext4 partitions.

```
============================= Boot Info Summary: ==============================

 => Grub0.97-os.1 is installed in the MBR of /dev/sda and looks on boot drive 
    #1 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb25db25d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  83 Linux
/dev/sda2              96,390     2,200,904     2,104,515  82 Linux swap / Solaris
/dev/sda3    *      2,200,905    79,264,709    77,063,805  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: LABEL="GRUB" UUID="f63d2534-3088-446e-b13e-9b8e8092a956" TYPE="ext2" 
/dev/sda2: UUID="ac4e292e-6755-4774-a9d8-12bd85afaa30" TYPE="swap" 
/dev/sda3: UUID="61b08211-7fb3-4ae4-921e-19a86586e5ed" TYPE="ext4" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
[CENTER][/CENTER]
```

---

### Post by CardPlay3r on 2009-08-17
You need to set grub up again. This link should help [http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/](http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/)

---

### Post by presence1960 on 2009-08-17
when you installed ubuntu did you highlight the sda1 partition and click edit to set parameters for sda1 most importantly set mountpoint to /boot? If you did not then your boot files are not in that partition and even if you reinstall GRUB you will not be able to boot from sda1. If you didn't set sda1 as /boot during the install your files needed to boot are on the sda3 partition and you will have to boot from sda3.

P.S. The reason I say use linux terminolgy is because C:, D:, E:, etc. can be on the same hard disk or on another hard disk and the partitions may not be in order on a hard disk. With linux partition nomenclature there is no doubt what disk the partitions are on and in what order they are.

I would get a 9.04 Live CD or USB and run the boot info script again as you are missing a lot of info since it can't read ext 4. I can't make heads or tails out of that output.

---

### Post by sandy8925 on 2009-08-22
ok i'll do that. supergrub didn't work either.

---

### Post by sandy8925 on 2009-09-09
Just thought I would say that I've solved my problem. Supergrub didn't work but I downloaded jaunty desktop iso,burned,booted and reinstalled grub (all thanks to herman's grub page - the best grub resource i've ever seen!)

---

### Post by raymondh on 2009-09-09
> **sandy8925 said:**
> Just thought I would say that I've solved my problem. Supergrub didn't work but I downloaded jaunty desktop iso,burned,booted and reinstalled grub (all thanks to herman's grub page - the best grub resource i've ever seen!)

Excellent news ..... ditto on herman's site.  The BOOT-INFO-SCRIPT as well is a great resource to have and use as it shows the operator the "whole picture". 

Happy Ubuntu-ing.

---

