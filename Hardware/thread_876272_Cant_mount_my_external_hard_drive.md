---
title: "Cant mount my external hard drive"
date: 2008-07-31
forum: Hardware
---

### Post by thebender on 2008-07-31
Hello. 

I just installed Ubuntu for amd 64 on my acer aspire 5100. 

When I plugged in my Western Digital external hard drive, Ubuntu told me 
"cannot mount volume. Invalid mount option when attempting to mount the volume 'My Book'."

here is what i get when i type in "sudo fdisk -l"


> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9402    75521533+  83  Linux
/dev/sda2            9403        9729     2626627+   5  Extended
/dev/sda5            9403        9729     2626596   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS


ntfs-3g is installed...

I am thankful for every help!
Dennis

---

### Post by thebender on 2008-07-31
i just found the problem. the hard drive was mounted as a cd rom drive.. i fixed it

greez

---

### Post by stompy11 on 2008-07-31
this could be my problem how do you fix?

---

### Post by thebender on 2008-07-31
hi.

i checked sudo fstab

```
sudo nano /etc/fstab
```

my external drive was set as cdrom0. i put a # infront of it, saved and went out. 

then i mounted it again.

```
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o umask=000
```

worked fine for me. 

i tried to find the original post but i dont find it anymore. sorry for that.

---

