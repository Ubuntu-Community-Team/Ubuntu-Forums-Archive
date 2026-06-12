---
title: "I need help mounting my drives"
date: 2008-08-30
forum: Hardware
---

### Post by neko-master on 2008-08-30
Hey ppl, im new to linux and recently installed it on my 2nd hard drive since I still need windows for Various things. Anyways, when I try to access (mount) my 1st hard drive (the one with windows) and/or my 3rd Drive, it says cannot mount drive.

Can somebody help me with this as I rlly wanna use linux more but this is detouring me away from using linux more.
Is there some way I have to Boot up or is there a program that will auto mount and/or force mount other drives.

---

### Post by fwre01 on 2008-08-30
Can you provide the output from ```
 mount 
``` and ```
 sudo fdisk -l 
```

---

### Post by neko-master on 2008-08-30
> **fwre01 said:**
> Can you provide the output from ```
 mount 
``` and ```
 sudo fdisk -l 
```

Ok, I'll try, dont flip out if this aint the stuff : (

\/ \/ \/ Mount \/ \/ \/
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/nekomaster/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nekomaster)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=nekomaster)
/dev/sde1 on /media/USB DISK 2 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdf1 on /media/DSC_FATDISK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdd1 on /media/USB DISK 1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

\/ \/ \/ sudo fdisk -l \/ \/ \/
Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4862    39053983+   7  HPFS/NTFS

Disk /dev/sdb: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9800481f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1744    14008648+  83  Linux
/dev/sdb2            1745        1826      658665    5  Extended
/dev/sdb5            1745        1826      658633+  82  Linux swap / Solaris

Disk /dev/sdc: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5a5abd68

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         787     6321546    7  HPFS/NTFS

Disk /dev/sdd: 1030 MB, 1030750208 bytes
16 heads, 32 sectors/track, 3932 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        3932     1006576    b  W95 FAT32

Disk /dev/sde: 1040 MB, 1040187392 bytes
65 heads, 32 sectors/track, 976 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         977     1015792    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(992, 64, 32) logical=(976, 47, 32)

Disk /dev/sdf: 3 MB, 3146240 bytes
2 heads, 16 sectors/track, 192 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         192        3066+   1  FAT12

There, I hope that helps, btw, the 3MB disk is my camera : P

---

### Post by SuperSonic4 on 2008-08-30
> **neko-master said:**
> Hey ppl, im new to linux and recently installed it on my 2nd hard drive since I still need windows for Various things. Anyways, when I try to access (mount) my 1st hard drive (the one with windows) and/or my 3rd Drive, it says cannot mount drive.

Can somebody help me with this as I rlly wanna use linux more but this is detouring me away from using linux more.
Is there some way I have to Boot up or **is there a program that will auto mount and/or force mount other drives**.

Have you tried mounting as root? To do so type ```
gksudo nautilus
``` into a terminal, then type or navigate to ```
/media
``` right click and select mount.

To answer the bit in bold you get ntfs-config, type ```
sudo apt-get install ntfs-config
``` in a terminal or use the repos although it will mount only ntfs drives. As for force mounting, you only need to do it after an unclean windows shutdown. The best solution is to go into windows and shut it down properly but you can type ```
sudo mount -t ntfs-3g /dev/[COLOR="Red"]sda1[/COLOR] /media/[COLOR="Red"]*<folder name>*[/COLOR] -o force
```

[COLOR="Red"]sda1[/COLOR] is just an example (although I think it's your windows drive, right click in nautilus to check for sure.

**Only type the above code if *nothing* else works and check you need to do it first, an error message will usually come up if it was an unclean shutdown.**

And a 3MB camera? Does it fit *any* pictures on :p

---

### Post by fwre01 on 2008-08-30
OK. 

from a terminal type "sudo gedit /etc/fstab" then add these two lines at the bottom

```
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0   0
/dev/sdc1   /media/sdc1   ntfs-3g   defaults,locale=en_US.utf8   0   0
```

save it. Then create those two dirs ```
mkdir /media/sda1 
mkdir /media/sdc1
``` then type ```
sudo mount -a
``` this should mount those two drives on dirs /media/sda1 and /media/sdc1. and everytime your PC boots.

hope that works for ya!

---

### Post by neko-master on 2008-08-30
> **SuperSonic4 said:**
> Have you tried mounting as root? To do so type ```
gksudo nautilus
``` into a terminal, then type or navigate to ```
/media
``` right click and select mount.

To answer the bit in bold you get ntfs-config, type ```
sudo apt-get install ntfs-config
``` in a terminal or use the repos although it will mount only ntfs drives. As for force mounting, you only need to do it after an unclean windows shutdown. The best solution is to go into windows and shut it down properly but you can type ```
sudo mount -t ntfs-3g /dev/[COLOR="Red"]sda1[/COLOR] /media/[COLOR="Red"]*<folder name>*[/COLOR] -o force
```

[COLOR="Red"]sda1[/COLOR] is just an example (although I think it's your windows drive, right click in nautilus to check for sure.

**Only type the above code if *nothing* else works and check you need to do it first, an error message will usually come up if it was an unclean shutdown.**

And a 3MB camera? Does it fit *any* pictures on :p



> **fwre01 said:**
> OK. 

from a terminal type "sudo gedit /etc/fstab" then add these two lines at the bottom

```
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0   0
/dev/sdc1   /media/sdc1   ntfs-3g   defaults,locale=en_US.utf8   0   0
```

save it. Then create those two dirs ```
mkdir /media/sda1 
mkdir /media/sdc1
``` then type ```
sudo mount -a
``` this should mount those two drives on dirs /media/sda1 and /media/sdc1. and everytime your PC boots.

hope that works for ya!

Ok, none of the above methodes worked since Im no good with Command Prompt stuff, if anyone has a messenger that supports giveing me help through remote assistance then please IM me at eitehr
[email]detrix_x@yahoo.ca[/email]
[email]detrix_x@hotmail.com[/email]

---

### Post by nicedude on 2008-08-30
Try pysdm to mount them for you

Install command

sudo apt-get install pysdm

Command to run

sudo pysdm

Once inside select disk & partition in the left hand side of GUI and then click mount


Hope that works :-)

---

