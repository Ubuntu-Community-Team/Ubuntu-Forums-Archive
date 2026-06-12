---
title: "mount internal hard drive"
date: 2008-09-28
forum: Hardware
---

### Post by amewnorian on 2008-09-28
I have an internal hard drive, and I'd like to be able to use it like a big folder, sort of like a usb that's always plugged in... If possible, I'd like it to be able to be accessed from any operating system i might feel like installing in the future (although I don't know if what I'm doing now does that) If there's a better way, tell me please, lol...

I've gotten as far as creating a partition (sdc1). Then, I followed the instructions here, [http://ubuntuforums.org/showthread.php?t=560015]("http://ubuntuforums.org/showthread.php?t=560015")

so I did this:

```
amewnorian@amewnorian-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078bd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59418   477275053+  83  Linux
/dev/sda2           59419       60801    11108947+   5  Extended
/dev/sda5           59419       60801    11108916   82  Linux swap / Solaris

Disk /dev/sdb: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45214520

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2501    20089251   83  Linux

Disk /dev/sdc: 20.5 GB, 20520493056 bytes
255 heads, 63 sectors/track, 2494 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066632

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2494    20033023+  83  Linux
```

Then:

```
amewnorian@amewnorian-desktop:~$ sudo vol_id -u /dev/sdc1
3c2d9ecb-46e7-455e-9703-29fefe68ebde
```

Then I add the following to /etc/fstab:

```
amewnorian@amewnorian-desktop:~$ UUID=3c2d9ecb-46e7-455e-9703-29fefe68ebde /media/sdc1 ext3 auto,utf8,umask=007,uid=amewnorian,gid=amewnorian 0 0
```

Then, I make a directory and try to mount it:

```
amewnorian@amewnorian-desktop:~$ sudo mkdir /media/sdc1
amewnorian@amewnorian-desktop:~$ sudo mount /media/sdc1
mount: special device /dev/disk/by-uuid/3c2d9ecb-46e7-455e-9703-29fefe68ebde does not exist
```

And now I have no idea what to do...

---

### Post by ajgreeny on 2008-09-28
If you format the disk (partition) to either fat32 (win 95 and above) or ntfs (win xp and above) it will be OK for both windows and linux, but I'm not sure about mac systems at all, so no help there, I'm afraid.  You then need to mount it at boot time by adding an appropriate line to the /etc/fstab file in the pattern of one of the following lines:-

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

Use the first for fat32 and the second for ntfs partitions but remember to make the mount point first (*/media/windows* in my example) and to change the device name to your partition's own device name.  There is no need to use the UUID unless you really want to, the device name will work OK.

---

### Post by prshah on 2008-09-28
> **amewnorian said:**
> Then, I make a directory and try to mount it:
```
amewnorian@amewnorian-desktop:~$ sudo mkdir /media/sdc1
amewnorian@amewnorian-desktop:~$ sudo mount /media/sdc1
mount: special device /dev/disk/by-uuid/3c2d9ecb-46e7-455e-9703-29fefe68ebde does not exist
```


I believe the mount directory (/media/sdc1) has to be root-owned (which it is with the above command) and should be in "plugdev" group (which it won't with the above command). Try changing the group of the directory created to "plugdev"```
sudo chown root:plugdev /media/sdc1
``` and, mount it with gid=46 (group id for plugdev, should be the same on all systems). Also, add "defaults" for proper settings for ext3 (eg, relatime)```
UUID=3c2d9ecb-46e7-455e-9703-29fefe68ebde /media/sdc1 ext3 defaults,auto,utf8,umask=007,uid=amewnorian,gid=46 0 0
```

---

