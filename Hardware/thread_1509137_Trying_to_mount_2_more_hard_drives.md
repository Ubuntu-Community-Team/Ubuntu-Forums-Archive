---
title: "Trying to mount 2 more hard drives"
date: 2010-06-13
forum: Hardware
---

### Post by marcoftheknight on 2010-06-13
Hi,

I recently installed 2 new sata 3GS Hard drives and followed one of the documentations online about adding hard drives but it failed miserably and I think it was because I had previously installed LVM ( woops) now I need to know what the heck I have to do to get these hard drives up and running an be able to see them as just regular hard drives partitioned with ext3 just want to be able to add video and music to these hard drives.
Heres some of my code what else should I do ( I tried creating new Volume groups on my hard drives both of them and they still don't seem to show up.)
any idea would help even telling me what ive done would be nice to so I can understand a little bit or dirrect me to info on the lvm software ( I am running ubuntu 10.04 LUcid.


-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000904a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59322   476502016   83  Linux
/dev/sda2           59323       60802    11882497    5  Extended
/dev/sda5           59323       60802    11882496   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77826   625131863+  8e  Linux LVM

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77826   625131863+  8e  Linux LVM

why cant I mout them 

 sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by garvinrick4 on 2010-06-13
Go to gparted and right click on the drive you want to format and choose the format you want ext3, ext4. and then click on green arrow on top of page to apply.

In gparted you can see all 3 of your drives. I do not know what version ubuntu you are using but if for any reason do not have gparted.

```
sudo apt-get install gparted
```You can give them a label while you are there it is easier to work with them when labeled.
They will have a mount point of like /media/data or /media/storage whatever you want.
Cannot label a drive that is mounted so if you want to label your OS installed use a Live CD. 
When you right click on drive partition you will see label.
Click on upper left gparted and go down to devices to see all your drives installed. Later versions upper right also has drop down menu to get to drives.

---

### Post by marcoftheknight on 2010-06-13
Cool Gparted works wonders I wonder why it didnt work when I put the code in using fdisk. may have been the LVM flag which with gparted I was able to take out I have no idea how I would do this other wise. Gparted is really hand would be nice to see the code running in the background.

Hey how do you think I should run my hardrive to optimize computer performance do you think I should try to get RAID running for my 3 hard drives so that I can improve system performance maybe run a small internet server?

---

### Post by garvinrick4 on 2010-06-14
> **marcoftheknight said:**
> Cool Gparted works wonders I wonder why it didnt work when I put the code in using fdisk. may have been the LVM flag which with gparted I was able to take out I have no idea how I would do this other wise. Gparted is really hand would be nice to see the code running in the background.

Hey how do you think I should run my hardrive to optimize computer performance do you think I should try to get RAID running for my 3 hard drives so that I can improve system performance maybe run a small internet server? I have never had a raid setup but sure someone around has. Have a nice day.

---

