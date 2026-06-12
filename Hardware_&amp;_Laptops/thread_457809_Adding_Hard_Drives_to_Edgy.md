---
title: "Adding Hard Drives to Edgy"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by buckweat420 on 2007-05-29
I have a Ubuntu 6.10 Server that I use and a Samba File Server to store computer backup`s on. It has a 320 GB hard drive that Ubuntu is installed on and the /shares directory is where I store all the backup`s. The 320 is full so I added 2x40 GB and 1x80 GB hard drives to it, FDISK them and formatted them using ReiserFS. What I want to do is use these 3 hard drives to add more storage to the /shares directory. I have allready tried mounting the drives to /shares but when i do this the files that are on the 320 drive in the shares folder disappear after mounting another hard drive to the /shares directory. How can i make it so that all the drives are used as one big one. I have Webmin installed and when I go under Linux Raid it says "The kernel RAID status file /proc/mdstat does not exist on your system. Your kernel probably does not support RAID." Please help me if you can!!!!

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       38728   311082628+  83  Linux
/dev/hda2           38729       38913     1486012+   5  Extended
/dev/hda5           38729       38913     1485981   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4863    39062016   83  Linux

Disk /dev/hdc: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        4863    39062016   83  Linux

Disk /dev/hdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       10011    80413326   83  Linux

---

### Post by buckweat420 on 2007-05-29
My friend has did this before and he said he used logical drives and a jbod raid and thats what I want to do, Please help!

Thanks again for looking,
Chad

---

### Post by buckweat420 on 2007-05-29
*bump*

---

