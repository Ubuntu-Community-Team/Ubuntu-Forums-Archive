---
title: "New Hard Drive won't mount on boot."
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by davbren on 2007-12-27
Hey, I just installed a new hdd, theres not much on it but it won't mount on boot i.e. won't appear on the desktop by default... I can mount it by going through the computer section. Any ideas?

---

### Post by c0mp13371331337 on 2007-12-27
Sounds like you just need to add a line to your /etc/fstab document.

For example, my slave drive needed a line in fstab so it would mount:

```

/dev/sdb1   /home/me/Videos     ext3    defaults        0       2
```

In your case, sdb1 may not be sdb1, check your /dev directory to see what your new drive would be, probably sdb* or hdb*.

And where mine says /home/me/Videos, change that to the directory you'd like the drive mounted to.

---

### Post by davbren on 2007-12-27
Hey thanx for the help.. I'm sorry though, with things like this I'm an absolute noob. I don't know what type of drive it is and what its name is...

---

### Post by davbren on 2008-03-24
Ok I've tried playing about with it and I really dont have a clue what Im doin...

---

### Post by jslman on 2008-03-24
```

sudo fdisk -l

```

This will show you what drives you have installed and what partitions are installed on it, here is the output for my laptop with usb external disk attached.

```

jeroen@portable-pinguin:~$ sudo fdisk -l
[sudo] password for jeroen:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x611ce76c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2681     2000092+  82  Linux swap / Solaris
/dev/sda4            2682       12161    76148100    5  Extended
/dev/sda5            3652       12161    68356543+  83  Linux
/dev/sda6            2682        3651     7791462   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000011d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39070048+  83  Linux

```

You can see I have two disks, /dev/sda and /dev/sdb.

If you now know what your new harddrive is named like just do the following:

```

sudo nano /etc/fstab

```

Now add the line mentioned earlier in this post:

```

/dev/sdb1   /home/me/Videos     ext3    defaults        0       2

```

for more info on the file fstab:

```

man fstab

```

If you do not have any partitions yet you can install gparted 

```

sudo apt-get install gparted

```.

This is a graphical application to partition your disk.

Jeroen

---

