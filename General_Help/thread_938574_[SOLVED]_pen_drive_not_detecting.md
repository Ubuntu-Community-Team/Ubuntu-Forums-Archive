---
title: "[SOLVED] pen drive not detecting"
date: 2008-10-05
forum: General Help
---

### Post by suhaib1thariq on 2008-10-05
i have hardy........my pen drive is not mounting...in hardy...how can i mount it

---

### Post by Elfy on 2008-10-05
When you plug it in do you get an error - please post the error message if there is one.

---

### Post by suhaib1thariq on 2008-10-05
it shows "cannot mount volume
             Invalid mount option when attempting to mount the volume 'kingston'.

---

### Post by Elfy on 2008-10-05
Can you plug the drive in and run these, post the outputs please

```
sudo fdisk -l
df -h
```

Also please don't double post

---

### Post by suhaib1thariq on 2008-10-06
it is my resukt of "sudo fdisk -l" after i plug the pen drive

"suhaib@suhaib-desktop:~$ sudo fdisk -l
[sudo] password for suhaib: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d471d46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       30401   203238315    f  W95 Ext'd (LBA)
/dev/sda5            5100       11473    51199123+   7  HPFS/NTFS
/dev/sda6           11474       17847    51199123+   7  HPFS/NTFS
/dev/sda7           17848       24221    51199123+   7  HPFS/NTFS
/dev/sda8           24222       29935    45897673+  83  Linux
/dev/sda9           29936       30401     3743113+  82  Linux swap / Solaris

Disk /dev/sdf: 4020 MB, 4020240384 bytes
92 heads, 27 sectors/track, 3161 cylinders
Units = cylinders of 2484 * 512 = 1271808 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           4        3162     3921920    b  W95 FAT32"



and output of df -h is:

"suhaib@suhaib-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              44G  2.9G   39G   7% /
varrun                950M  100K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   84K  950M   1% /dev
devshm                950M   12K  950M   1% /dev/shm
lrm                   950M   38M  913M   4% /lib/modules/2.6.24-16-generic/volatile
/dev/sda7              49G  991M   48G   2% /media/sda7
/dev/sda6              49G   15G   35G  31% /media/sda6
/dev/sda5              49G  476M   49G   1% /media/sda5
/dev/sda1              40G  7.8G   32G  20% /media/SUHAIB
gvfs-fuse-daemon       44G  2.9G   39G   7% /home/suhaib/.gvfs"


what can i do?

---

### Post by Elfy on 2008-10-06
See if it mounts manually

```
sudo mkdir /mnt/tmp
sudo mount -t vfat /dev/sdf1 /mnt/tmp -o uid=1000,gid=100,utf8,dmask=027,fmask=137
```

See if it mounts now - if there is an error in terminal please copy and paste it.

---

### Post by suhaib1thariq on 2008-10-06
the output of sudo mkdir /mnt/tmp   is 


"suhaib@suhaib-desktop:~$ sudo mkdir /mnt/tmp
[sudo] password for suhaib: 
mkdir: cannot create directory `/mnt/tmp': File exists"


and output of  sudo mount -t vfat /dev/sdf1 /mnt/tmp -o uid=1000,gid=100,utf8,dmask=027,fmask=137   is
 

"suhaib@suhaib-desktop:~$ sudo mount -t vfat /dev/sdf1 /mnt/tmp -o uid=1000,gid=100,utf8,dmask=027,fmask=137
mount: /dev/sdf1 already mounted or /mnt/tmp busy
mount: according to mtab, /dev/sdf1 is already mounted on /mnt/tmp"



but the device is mounting now....after this code ...how it is?..what is the problem? ...will it be permanent change...and mount always

---

### Post by suhaib1thariq on 2008-10-06
thanks....it smounting now ....please reply....why it is not mounting previously.....

---

### Post by suhaib1thariq on 2008-10-06
it is not mounting after  i restarted the system.........
how can i make it permanent

---

### Post by Elfy on 2008-10-06
> /dev/sdf1 already mounted or /mnt/tmp busyit would seem that it was already mounted - wher do you look to say that it isn't mounted. I s it not showing on nautilus when you plug it in?

---

### Post by Julius1988 on 2008-10-06
Thanks forestpixie for ur reply........i have the same issue to, i followed ur instruction and i was able to mount my pen drive but the change is not permanent after i restart i again get the error invalid mount option after i plugin my pendrive........it is showing up in nautilus, but when i dbl clk that an error pops out reporting " invalid mount option when attempting to mount the volume"

---

### Post by suhaib1thariq on 2008-10-06
it seems it mounted .......but when i plug in the pen drive it shows ...cannot mount volume....invalid mount option when attempting to mount suhaib....
that pendrive is not opening.....
after i executed your previous code ....it opens... when i restarted the system ...it again not mounting ...
how can i solve this

---

### Post by Elfy on 2008-10-06
Can you plug in the drive and opena terminal, run these 2 commands and post the output please. Also I assume you have a cd/dvd drive - if that is not the case please advise

```
cat /var/log/dmesg |tail -n 40
gnome-mount -v -b -d /dev/sdf1
cat /etc/fstab
```

Please surround pasted output with code tags - [noparse]```
at start and 
```at the end[/noparse]

---

### Post by suhaib1thariq on 2008-10-06
when i mount the pen drive it shows cannot mount volume ...and my fstab file looks like

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda8 :
UUID=1b5bae7b-b3c2-4266-83a7-0680463f6549 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda9 :
UUID=4de4a5d3-06b6-475c-8db9-711dd1a15515 none swap sw 0 0
/dev/sdf1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda7 /media/sda7 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda6 /media/sda6 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/SUHAIB ntfs-3g defaults,locale=en_US.UTF-8 0 0

how can i mount pen drive

---

### Post by Julius1988 on 2008-10-06
> 
/dev/sdf1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

change the udf to vfat.
now plugin ur pen drive and see. I think its problem that arises as a result of installing ubuntu from pen drive.

---

### Post by suhaib1thariq on 2008-10-06
thanks .problem solved........its mounting now

---

### Post by janutomo on 2011-08-04
Hi,
I have similiar problem with this thread, but in my case USB Flash Disk cannot detect by PC, this is the list :
> janu@ppic01:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              28G  7.0G   19G  27% /
none                  746M  284K  746M   1% /dev
none                  750M  368K  750M   1% /dev/shm
none                  750M  516K  750M   1% /var/run
none                  750M     0  750M   0% /var/lock
none                  750M     0  750M   0% /lib/init/rw
/dev/sda6              39G   21G   18G  53% /media/DATA

> janu@ppic01:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7bae28b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         243     1951866   82  Linux swap / Solaris
/dev/sda3             244        9729    76196295    5  Extended
/dev/sda5            8805        9729     7430031    7  HPFS/NTFS
/dev/sda6            3838        8804    39897396    b  W95 FAT32
/dev/sda7             244        3836    28860709+  83  Linux

Partition table entries are not in disk order


I use Ubuntu 10.04

Thanks

---

### Post by glene77is on 2011-08-04
For several months, I have a pendrive for bootup occassionally, in order to load Puppy Linux.
I had to set my Post Delay to 10 seconds, so that the USB pendrive could chargeup.
Then when the real boot occurred it was ready to respond.  
Sometimes, have to make sure there were no other USB devices attached. 
Works most of the time.  Pendrives are not perfect. 

[ Now,    I have installed Puppy as Frugal, along with Parted-Magic, Tiny-Core, and Ubuntu 10,  
controlled by Grub2.    I always use a Squashfile based OS for internet access, such as Puppy.  ]

---

### Post by Wim Sturkenboom on 2011-08-04
> **janutomo said:**
> Hi,
I have similiar problem with this thread, but in my case USB Flash Disk cannot detect by PC, this is the list :

Please post output of *_dmesg |tail -n 15_* (immediately after you've inserted the memory stick) as well as *_lsusb_*. Place the output between [noparse] ```
 and 
```[/noparse] instead of [noparse]>  and [/noparse].

By the looks of it (fdisk output), it's not detected at all. Also, if you have access to another PC, is it working in there? Just to prevent us from fixing a problem that is caused by a broken stick ;)

---

### Post by janutomo on 2011-08-05
Hi,
This is the output of $dmesg |tail -n 15
```
root@ppic01:/home/janu# dmesg |tail -n 15
[   21.880136] CPU0 attaching sched-domain:
[   21.880142]  domain 0: span 0-1 level CPU
[   21.880147]   groups: 0 1
[   21.880156] CPU1 attaching sched-domain:
[   21.880159]  domain 0: span 0-1 level CPU
[   21.880163]   groups: 1 0
[   30.700009] eth0: no IPv6 routers present
[  849.892056] usb 1-7: new high speed USB device using ehci_hcd and address 2
[  850.107594] usb 1-7: configuration #1 chosen from 1 choice
[  850.159060] Initializing USB Mass Storage driver...
[  850.159480] scsi4 : SCSI emulation for USB Mass Storage devices
[  850.159659] usbcore: registered new interface driver usb-storage
[  850.159667] USB Mass Storage support registered.
[  850.160552] usb-storage: device found at 2
[  850.160556] usb-storage: waiting for device to settle before scanning
root@ppic01:/home/janu# 
```

Thanks

---

### Post by Wim Sturkenboom on 2011-08-05
Wait a little bit longer ;) You should get more (including something that refers to sdX :sdXY (where X = a, b, c, ... and Y = 1, 2, 3)

Something is detected, but not ready to use yet. What is the output of lsusb?

Not sure if I can help further :(

---

