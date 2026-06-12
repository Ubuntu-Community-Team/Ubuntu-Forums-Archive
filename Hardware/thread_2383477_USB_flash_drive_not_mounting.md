---
title: "USB flash drive not mounting"
date: 2018-01-25
forum: Hardware
---

### Post by ulissipus on 2018-01-25
I have one particular USB flash drive that will not mount in Xubuntu 16.04. It works perfectly inn Windows but with Xubuntu I always get this error message:

FAILED TO MOUNT "CINEMA"

Error mounting /dev/sdb1 at /media/lostados/cinema: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/lostados/cinema"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'


All my other USB drives work perfectly in Ubuntu and Windows.

Suggestion on what to do?

Tks

---

### Post by #&amp;thj^% on 2018-01-25
I'm guessing here that perhaps your USB might have been formatted with windows.
Did you ever see a message on Windows Like "Do You want to scan and Fix removable disk/USB"?
EDIT: I use something like this when manullay mounting USB Devices.
```
sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```
The options following the "-o" give you ownership of the drive, and the masks allow for extra security for file system permissions. If you don't use those extra options you may not be able to read and write the drive with your regular username. Use the correct location/path instead of  "sdb1"
If you need the correct path you can use:
```
sudo fdisk -l
```

---

### Post by Yellow Pasque on 2018-01-25
>  mount: unknown filesystem type 'exfat'

MAke sure you have exfat-utils package installed and maybe exfat-fuse package.

---

### Post by ulissipus on 2018-01-26
I'm a bit of a beginner and I'm afraid I didn't understand what Temujin said.

As to 1Fallen:
1. yes, USB drive was formatted with Windows - like all the others USB I have. They all work perfectly either in Windows or in Xubuntu;
2. yes, I do get that message from time to time. I just follow instructions and that is it. Have done it a couple of times in Windows with the USB that does not work in Xubuntu;
3. I did try following your advice, Here's what I got:

lostados@lostados:~$ sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
[sudo] password for lostados: 
mount: mount point /media/external does not exist

and

lostados@lostados:~$ sudo fdisk -l
Disk /dev/sda: 149,1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x097387ae

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 312580095 311578626 148,6G  5 Extended
/dev/sda5       1001472 312580095 311578624 148,6G 83 Linux


Disk /dev/mapper/sda5_crypt: 148,6 GiB, 159526158336 bytes, 311574528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/xubuntu--vg-root: 145,8 GiB, 156485287936 bytes, 305635328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/xubuntu--vg-swap_1: 2,8 GiB, 3011510272 bytes, 5881856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 119,3 GiB, 128043712512 bytes, 250085376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd2b63d37

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1          32 250085375 250085344 119,3G  7 HPFS/NTFS/exFAT
lostados@lostados:~$ 


best

---

### Post by Yellow Pasque on 2018-01-26
```
sudo apt-get install exfat-utils exfat-fuse
```

---

### Post by ulissipus on 2018-01-26
Please forget. I tried to format USB drive with Disks and I think I "killed" it: it is no longer recognized in Windows/Ubuntu.

No success in formatting it - either in Windows or Ubuntu...

Thanks all the same.

Best

---

### Post by wisjim2 on 2018-02-08
Installing the exfat utilities did the trick for me.  Whoopee!  :-))

---

