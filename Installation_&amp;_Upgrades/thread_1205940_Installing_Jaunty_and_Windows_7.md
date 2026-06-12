---
title: "Installing Jaunty and Windows 7"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Messyhair42 on 2009-07-06
So I just got my replacement HD from Seagate and i'm about to install it. I've decided to go with Jaunty again but keep EXT3. it's a 1 TB drive and i'd like to put about 20 GB aside for the windows 7 RC. can i do this as part of my regular formatting, and if so do i just leave 20000 MB as free space on the drive in order to install windows 7 afterwards? i'm doing this tonight so any help or recommendations are appreciated. I'm not so worried about GRUB because i can edit that later right?

---

### Post by Ra-Hoor-Khuit on 2009-07-06
Helpful linkage:  [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by raymondh on 2009-07-06
Win7 RC may only be about 11GB heavy ... but I think you need to give windows more "breathing room". 

Some links (albeit for Vista):

[http://www.bleepingcomputer.com/tutorials/tutorial133.html](http://www.bleepingcomputer.com/tutorials/tutorial133.html)
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Defrag first before shrinking 7

Good luck.

---

### Post by presence1960 on 2009-07-06
> **Messyhair42 said:**
> So I just got my replacement HD from Seagate and i'm about to install it. I've decided to go with Jaunty again but keep EXT3. it's a 1 TB drive and i'd like to put about 20 GB aside for the windows 7 RC. can i do this as part of my regular formatting, and if so do i just leave 20000 MB as free space on the drive in order to install windows 7 afterwards? i'm doing this tonight so any help or recommendations are appreciated. I'm not so worried about GRUB because i can edit that later right?

I did it both ways- leaving free space and creating partitions prior to any OS install. Win 7 would be a NTFS partition. Worked both ways for me on the 6 or so machines I set jaunty and Win 7 RC up on.

If you install Win 7 after Jaunty just remember windows will overwrite GRUB and you will have to restore it, which is easy. 
I am not sure id 20GB is enough, so check that out in the documentation. if you install some programs on there it may be tight. I have done it with a minimum of 40 GB. You have a 1 TB drive so what is another 10 or 20 GB?

---

### Post by Messyhair42 on 2009-07-06
my first attempt failed. i left 30GB unallocated for W7. on the same disk i have ubuntu 9.04 with / /usr /swap /tmp /var and /home as separate partitions. my problem comes as soon as i try to install W7 to the unallocated space after letting the setup know i want it put there as a primary partition. my guess is it's not working b/c the free space isnt NTFS but i'm not sure.

---

### Post by presence1960 on 2009-07-06
do you have room for another primary partition on your disk? You can only have 4, but an extended partition counts as one. If this is not the problem format the primary partition as NTFS then do the install.

---

### Post by Jormanks on 2009-07-06
you have to format the partition in where you are going to install win 7 with.... the format tool that win 7 has ¬¬
yeah, kind of pointless but it did it for me

---

### Post by Messyhair42 on 2009-07-06
here is the output of ```
sudo fdisk -l
``` for reference

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x622b854a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18715   150328206   83  Linux
/dev/sda2           18716       19457     5960115    5  Extended
/dev/sda5           18716       19457     5960083+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007fe0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         267     2144646   83  Linux
/dev/sdb2             268      117954   945320827+   5  Extended
/dev/sdb3          117955      121602    29294592    7  HPFS/NTFS
/dev/sdb5             268         753     3903763+  82  Linux swap / Solaris
/dev/sdb6             754        1239     3903763+  83  Linux
/dev/sdb7            1240        1506     2144646   83  Linux
/dev/sdb8            1507        1542      289138+  83  Linux
/dev/sdb9            1543      117954   935079358+  83  Linux

Disk /dev/sdc: 4007 MB, 4007657472 bytes
16 heads, 32 sectors/track, 15288 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x0002489b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15285     3912944   83  Linux

```

with /dev/sdb3 the destination of windows 7. i used gparted to format it from FAT16 (must have been the installation disk that did that) to NTFS

i did use the tool and it leaves me in the same place

---

### Post by presence1960 on 2009-07-06
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007fe0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         267     2144646   83  Linux
[COLOR="Red"]/dev/sdb2             268      117954   945320827+   5  Extended
/dev/sdb3          117955      121602    29294592    7  HPFS/NTFS
/dev/sdb5             268         753     3903763+  82  Linux swap / Solaris
/dev/sdb6             754        1239     3903763+  83  Linux
/dev/sdb7            1240        1506     2144646   83  Linux
/dev/sdb8            1507        1542      289138+  83  Linux
/dev/sdb9            1543      117954   935079358+  83  Linux
[/COLOR]

you are trying to install Windows to an extended partition. it needs to be in a primary partition. Even if it would install you will be pulling your hair out trying to get it to boot.

Also when you finally do go to insttall win 7 make sure the disk you are installing it onto is set as first boot in the HDD boot order in BIOS. If not when the install goes to write the bootloader it will try to write to the other disk which is Linux and you will get an error message. Windows will always put the bootloader on the MBR of the drive booting first.

---

### Post by Messyhair42 on 2009-07-06
the windows 7 installation tells me it's a primary partition. what do i need to do? it's brand new setup so it's not unthinkable to format all of /dev/sdb in order to get it to work

---

### Post by thiebaude on 2009-07-06
The best way to do it would be to install windows 7 then install ubuntu and when you get to the patitioning part you can decide how much space you want to have for ubuntu.I've done many dual-boots before and that way of doing it always works for me with no problems.I always used the Ubuntu Live CD.

---

### Post by presence1960 on 2009-07-06
> **Messyhair42 said:**
> the windows 7 installation tells me it's a primary partition. what do i need to do? it's brand new setup so it's not unthinkable to format all of /dev/sdb in order to get it to work

Check from Ubuntu in gparted to see if it is a primary partition or inside the extended partition.

---

### Post by Messyhair42 on 2009-07-06
gparted screenshot of /dev/sdb with /sdb3 highlighted

---

### Post by presence1960 on 2009-07-06
Ok so it is a primary partition. I am stumped here. I have installed Win7 on a few machines with jaunty for myself and others with no hassles. I would really hate to see you remove your Linux installs just to add Windows. In my mind that is an unfair trade off. Keep us posted so we can learn from this too.

---

### Post by Messyhair42 on 2009-07-06
i'm hesitant to do anything from the windows dvd. i've got two other ubuntu installations connected. /dev/sda contains Intrepid which i've been using since my last HD went down and it's what i'm using until i get the other drive setup right, and /dev/sdc is a flash drive with Jaunty and because of a wierd configuration of GRUB is the only way i can boot into Intrepid (i'll work on resolving that later, i.e. get the Intrepid entry into the new installation's GRUB, didn't work on the installation) so i might try tomorrow formatting sdb and installing windows first. I'm not really all that interesting in using Windows save for installing Photoshop, and it will stop working sooner than later unless i actually get W7

---

### Post by TSWMIN85 on 2009-07-06
I gave Windows 7 15 GB and it's working fine for me.

:guitar:

---

### Post by Messyhair42 on 2009-07-06
looking back at gparted just after getting to the partitioning with windows it says 3 GB used. could that be the problem? i told windows to format /sdc3 and there's still data there.

---

### Post by Messyhair42 on 2009-07-07
I used my LiveCd to create a new partition table on /sdb essentially wiping it. tried W7 disk again and getting the same error "Setup is unable to locate a partition" or something to that effect. i'll put it on hold for now and just get Jaunty running like i want it and leave some free space to be fiddled with later. thanks for your help everybody, alas, windows and i were just not meant to be

---

