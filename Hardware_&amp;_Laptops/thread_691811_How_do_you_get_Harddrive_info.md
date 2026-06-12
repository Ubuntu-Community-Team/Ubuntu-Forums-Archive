---
title: "How do you get Harddrive info?"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by whoopn on 2008-02-09
I am trying to manually edit grub (I dont need help with that, i understand that much).  I need to know the numbers of my harddrives (like hd0...h2..etc).  I know that the HD i am looking to tell grub about a boot loader on is sda1, however i dont know if thats hd3, or hd4 or what.  Here is the break down for my harddrives:

Internal:
Two SATAs:
Linux on one and windows on the other
One IDE:
That is the sda1 that i am looking for the info for

External:
Two USB (currently unplugged for simplicity with this stuff) HDs

Are there any commands for this or what?

Thanks in advance!

---

### Post by fenian on 2008-02-09
Go to the menu System>Prefrences>Hardware Information all your hardware (including drives) should be listed , click on the drive in the list and info for the drive will be displayed in the window.

---

### Post by logos34 on 2008-02-09
> **whoopn said:**
>  I know that the HD i am looking to tell grub about a boot loader on is sda1, however i dont know if thats hd3, or hd4 or what. 

look in /boot/grub/device.map

that will list the drives as they were seen at installation time.  (hd0) is always the boot drive, and is where grub is installed by default.  It's quite possible that grub is on the mbr of the IDE drive even though you put ubuntu on the second sata.  (grub gives prirority to the IDE channels)

---

### Post by cdtech on 2008-02-09
There are several command line args to display disk information. Two of which are:
```

fdisk -l
```
which is a partition table manipulator, output =
```
fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f29dfaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18359   147468636    7  HPFS/NTFS
/dev/sda2           18360       19457     8819685    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000116f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         638     5124703+  83  Linux
/dev/sdb2             639        8750    65159640    5  Extended
/dev/sdb3            8751       30401   173911657+   7  HPFS/NTFS
/dev/sdb5             639        1307     5373711   82  Linux swap / Solaris
/dev/sdb6            1308        6413    41013913+  83  Linux
/dev/sdb7            6414        8750    18771921   83  Linux
```
A second would be the df -h command:
```
df -h
```
Which gives an output =
```
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb7              18G  7.6G  9.6G  45% /
varrun                945M  108K  945M   1% /var/run
varlock               945M     0  945M   0% /var/lock
udev                  945M  104K  945M   1% /dev
devshm                945M  832K  944M   1% /dev/shm
lrm                   945M   38M  907M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             4.8G   30M  4.7G   1% /boot
/dev/sdb6              39G  1.3G   36G   4% /home
/dev/sda1             141G   63G   79G  45% /media/sda1
/dev/sda2             8.5G  6.9G  1.6G  82% /media/sda2
/dev/sdb3             166G   49G  118G  30% /media/Storage
/dev/hda              7.9G  7.9G     0 100% /media/cdrom0
```
SATA drives are listed as sda, sdb etc...which are the same as hd0, hd1 respectivly. If you use two seperate hard drives and grub is installed on its own, it see's that drive as hd0 (although it could be the second hard drive in your system). USB devices are listed using the command line arg **lsusb**

---

### Post by whoopn on 2008-02-09
Thank you, i will try those.  I already tried df and fdisk but they wouldn't get me the info.  I'll try the device info viewer and device.map file.

Thanks guys.

---

### Post by Yellow Pasque on 2008-02-09
Also: 
```
sudo lshw -businfo -C disk
```

---

### Post by whoopn on 2008-02-09
thx Temujin...that's a helpful command.

---

