---
title: "I Lost My Original Mountpoints After Adding New Hard Drive"
date: 2010-02-13
forum: Hardware
---

### Post by bper on 2010-02-13
I previously had 2 250 GB SATA hard drives and added a 1 TB hard drive. Running Ubuntu 9.10 64bit. 4MB RAM.

After adding the drive, it was recognized by the BIOS, and I partitioned it with gparted. I checked to make sure that the right device was referenced in gparted and then formated the 1 TB drive.

I created a directory for the mount point and I edited the /etc/fstab to mount the drive on reboot. This is the line that I added to the bottom of fstab:

/dev/sda1 /media/abc ext3 defaults 0 2

The device that I used came directly from gparted, which is what was referring to the new 1 TB drive.

After I rebooted, I could mount the new drive, but the previous mount points were not available. My boot drive is referred in gparted as /dev/mapper/.... and the second drive gives the following warnings:
e2label: No such file or directory while trying to ope /dev/sdb1. Couldn't find valid filesystem superblock.

dumpe2fs: No such file or directory while trying to open /dev/sdb1

Unable to read the contents of this file system!
Because of this some operations may be unavailable

The data is still accessible because I can find it from the / partition (which is in /dev/mapper/...).

Here is the output of fdisk -l:

Device Boot Start End Blocks Id System
/dev/sda1 1 121601 976760001 83 Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9 72261 83 Linux
/dev/sdb2 10 763 6056505 82 Linux swap / Solaris
/dev/sdb3 764 794 249007+ 83 Linux
/dev/sdb4 795 30401 237818227+ 83 Linux

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

Device Boot Start End Blocks Id System
/dev/sdc1 1 30401 244196001 5 Extended
/dev/sdc5 1 30401 244195969+ 83 Linux

Is there anyway that I can fix my mount points? /dev/sdb1 does exist, but it is not a directory. What step did I miss with gparted?

Thanks.

---

### Post by Menthu_Rae on 2010-02-13
You should mount via UUID so that no matter the order of the drive (if it changes or you add other drives, etc) - it will always mount in the same spot. i.e.:

```
UUID=fcfcasfe-55af-428e-81c7-28035562a905 /               ext4    errors=remount-ro 	0       1
UUID=69asdtb8c67c-ffa1-3331-ac23-276c296100d5 /home           ext4    defaults        	0       2
```

You can find the UUID of your drive(s) via:

```
ls -ltra /dev/disk/by-uuid/
```

---

### Post by bper on 2010-02-13
Thanks for your response.

I'm unsure of how to read this and what to do next. How can I tell which UUID is which drive?
There are 3 total drives installed. 2 250s and 1 TB.
The following is the output of the ls -ltra /dev.disk/by-uuid:

total 0
lrwxrwxrwx 1 root root  10 2010-02-13 07:57 f587f1c0-4b9a-40fd-b6ef-1f47b9a3c121 -> ../../sda1
drwxr-xr-x 6 root root 120 2010-02-13 07:57 ..
lrwxrwxrwx 1 root root  29 2010-02-13 07:57 a0d88318-5afd-40a8-8e93-624cb0ba7d57 -> ../../mapper/nvidia_fhddbbhf4
lrwxrwxrwx 1 root root  29 2010-02-13 07:57 ce6f23e0-a907-4d9f-8c55-56df471906e3 -> ../../mapper/nvidia_fhddbbhf2
lrwxrwxrwx 1 root root  29 2010-02-13 07:57 72a21906-de5c-4b8d-b7bb-1c6e9a7fe427 -> ../../mapper/nvidia_fhddbbhf1
lrwxrwxrwx 1 root root  29 2010-02-13 07:57 0aadb108-44c1-4e30-b6b2-8b26f8f7443c -> ../../mapper/nvidia_fhddbbhf3
drwxr-xr-x 2 root root 140 2010-02-13 07:57 .

Thanks.

---

### Post by Menthu_Rae on 2010-02-13
> **bper said:**
> Thanks for your response.

I'm unsure of how to read this and what to do next. How can I tell which UUID is which drive?
There are 3 total drives installed. 2 250s and 1 TB.
The following is the output of the ls -ltra /dev.disk/by-uuid:

total 0
lrwxrwxrwx 1 root root  10 2010-02-13 07:57 f587f1c0-4b9a-40fd-b6ef-1f47b9a3c121 -> ../../sda1
drwxr-xr-x 6 root root 120 2010-02-13 07:57 ..
lrwxrwxrwx 1 root root  29 2010-02-13 07:57 a0d88318-5afd-40a8-8e93-624cb0ba7d57 -> ../../mapper/nvidia_fhddbbhf4
lrwxrwxrwx 1 root root  29 2010-02-13 07:57 ce6f23e0-a907-4d9f-8c55-56df471906e3 -> ../../mapper/nvidia_fhddbbhf2
lrwxrwxrwx 1 root root  29 2010-02-13 07:57 72a21906-de5c-4b8d-b7bb-1c6e9a7fe427 -> ../../mapper/nvidia_fhddbbhf1
lrwxrwxrwx 1 root root  29 2010-02-13 07:57 0aadb108-44c1-4e30-b6b2-8b26f8f7443c -> ../../mapper/nvidia_fhddbbhf3
drwxr-xr-x 2 root root 140 2010-02-13 07:57 .

Thanks.

There's probably an easier way to do this - but you need to associate the UUIDs with the mount points you want...

One way to do this is open up GPartEd. Select the drive from the dropdown list on the right. Then right click on the partition and select "information". It'll show you the UUID.

You can then link this with the drive name (/dev/sda, etc), drive size and drive label to determine what drive it is and set up the mount point you want in fstab. ;)

---

### Post by bper on 2010-03-03
Thanks for your response. Right clicking and selecting information does not reveal the UUID. It is blank.

---

