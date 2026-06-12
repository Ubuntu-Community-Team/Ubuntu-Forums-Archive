---
title: "USB problem"
date: 2010-11-29
forum: Hardware
---

### Post by shif on 2010-11-29
i installed ubuntu 10.10 yesterday but i have a problem, it doesnt read any usb devices, im new to linux so i dont know what it is supposed to happen, i plug in some usb headphones and nothing happens, same with a usb drive of 8gb, it doesnt say anything at all, any tips??

---

### Post by Hippytaff on 2010-11-29
with these devices plugged in, open a terminal (CTRL+ALT+T) and type
```

lsusb

```
and post the output :-)

also, with the usb drive plugged in what is the output of
```

df

```

:-)
Do the usb drives work with any other os (like windows?)

---

### Post by shif on 2010-11-29
```
arosemena@Shif-LINUX:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:070f Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
arosemena@Shif-LINUX:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3              9611492   2432456   6690796  27% /
none                   1020736       252   1020484   1% /dev
none                   1026336      1144   1025192   1% /dev/shm
none                   1026336        88   1026248   1% /var/run
none                   1026336         0   1026336   0% /var/lock

```

looks like it detects them, but how can i use them? i plugged in a kingston 8gb usb drive and a microsoft lifechat headset, im new to linux im used to access usb drives from the computer folder, am i supposed to do anything else to make it appear?

---

### Post by shif on 2010-11-29
ok i found this page [https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")
and it says that i need to run that command to check the name of my device and that it should be /div/sdb1 but it doesnt appear in the list but when i run lsusb it clearly shows that its connected

```


arosemena@Shif-LINUX:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcfce28df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        3481    27852800    7  HPFS/NTFS
/dev/sda3            3649        4864     9764864   83  Linux
/dev/sda4            3481        3649     1346561    5  Extended
/dev/sda5            3481        3649     1346560   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Hippytaff on 2010-11-30
Have you read the troubleshooting part of the this?
[https://help.ubuntu.com/community/Mount/USB#Troubleshooting](https://help.ubuntu.com/community/Mount/USB#Troubleshooting)

---

