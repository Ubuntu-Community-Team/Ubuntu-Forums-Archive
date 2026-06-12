---
title: "Unable to mount USB memory sticks"
date: 2009-01-20
forum: Hardware
---

### Post by joh31281 on 2009-01-20
When I plug a USB memory stick into my ubuntu 8.10 system, I get an error message saying the system cannot mount the drive

Here is the message I get:

Failed to execute child process "gnome-mount" (No such file or directory)

Any help would be appreciated.

Johnny

---

### Post by taurus on 2009-01-20
See if you can mount it by hand.  Open a terminal and post the output of this command here

```
sudo fdisk -l
```

Otherwise, you can try to reinstall gnome-mount again.

```
sudo apt-get update
sudo apt-get install gnome-mount
```

---

### Post by dark_harmonics on 2009-01-20
Sometimes an unclean ntfs disk will have issues. first do as the person above suggests.

```
 sudo fdisk -l 
```

Probably its listed as something like /dev/sdb1 (you can tell by how big it is)

I created a few mountpoints in my media share for things like this. To do that just type

```
 sudo mkdir /media/temp 
```

Then to mount the drive to that folder try

```
 sudo mount -o force /dev/sdb1 /media/temp 
```

---

### Post by joh31281 on 2009-01-20
> **taurus said:**
> See if you can mount it by hand.  Open a terminal and post the output of this command here

```
sudo fdisk -l
```

Otherwise, you can try to reinstall gnome-mount again.

```
sudo apt-get update
sudo apt-get install gnome-mount
```

I tried your suggestion - here is the output.

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4651a0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4676    37559938+  83  Linux
/dev/sda2            4677        4864     1510110    5  Extended
/dev/sda5            4677        4864     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 1020 MB, 1020788736 bytes
32 heads, 61 sectors/track, 1021 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      398636      983425   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       86419     1078237   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      957932     1949749   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     1478321     1478349       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1478320, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1478348, 22, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by taurus on 2009-01-20
Your 1GB thumbdrive is a big mess.  Do you have any valuable data on it?  If not, it's best to use gparted to delete all the partitions and then create a new one, /dev/sdb1, that takes up all 1GB of space.  Format it to fat32/vfat or ext3.

```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by joh31281 on 2009-01-20
> **taurus said:**
> See if you can mount it by hand.  Open a terminal and post the output of this command here

```
sudo fdisk -l
```

Otherwise, you can try to reinstall gnome-mount again.

```
sudo apt-get update
sudo apt-get install gnome-mount
```

I did the reinstall as you suggested and it works fine now.

Thanks!!

Johnny

---

### Post by dark_harmonics on 2009-01-22
Wow i dont think i ever saw a drive that messed up before. Glad to see you are fixed :)

---

