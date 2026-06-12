---
title: "/dev/sdd is not appearing when a hard drive is plugged in"
date: 2009-02-04
forum: Hardware
---

### Post by flippo on 2009-02-04
Hello,

I have a large cheap desktop I am using as a Mythbuntu/Dataserver box, with the standard 8.04 Mythbuntu install.  I have 3 USB external hard drives, all plugged in, but I only see three serial drives, normally not a problem, but I'm beginning to run out of space:

/dev/sda (my internal SATA II drive)
/dev/sdb (my XFS external)
/dev/sdc (my roomates NTFS external)

all of the drives are quite large, and I have a total of 5 things plugged into the 6 available USB ports, a keyboard, mouse printer and the three hard drives.

The machine is on a GIGabyte 945GCM-S2C mobo, with 2 front usb ports being used for the keyboard and mouse.

Thanks for any help, this one has me stumped.

---

### Post by jerome1232 on 2009-02-04
I think the actual output of these two commands should help, the second one will show all connected usb devices and should help in figuring out if it's even being picked up as connected. Run the last one a few seconds after connecting the misbehaving drive.

```
sudo fdisk -l
lsusb
cat /var/log/dmesg | tail
```

---

### Post by flippo on 2009-02-04
Ran the commands, it appears it isn't being detected at all, here are the outputs:

flippo@flippo-server:~$ sudo fdisk -l
sudo: unable to resolve host flippo-server
[sudo] password for flippo: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00015123

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       10942    68356575   83  Linux
/dev/sda3           10943       60302   396484200    5  Extended
/dev/sda4           60303       60801     4008217+  82  Linux swap / Solaris
/dev/sda5           10943       43914   264847558+  83  Linux
/dev/sda6           43915       60302   131636578+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS
flippo@flippo-server:~$ lsusb
Bus 005 Device 006: ID 04a9:1728 Canon, Inc. 
Bus 005 Device 005: ID 1058:0910 Western Digital Technologies, Inc. 
Bus 005 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
flippo@flippo-server:~$  cat /var/log/dmsg | tail
cat: /var/log/dmsg: No such file or directory
flippo@flippo-server:~$ cat /var/log/dmesg | tail
[   50.926131] EXT3 FS on sda1, internal journal
[   51.684650] kjournald starting.  Commit interval 5 seconds
[   51.684950] EXT3 FS on sda2, internal journal
[   51.684957] EXT3-fs: mounted filesystem with ordered data mode.
[   51.716055] kjournald starting.  Commit interval 5 seconds
[   51.716063] EXT3-fs: mounted filesystem with ordered data mode.
[   51.764297] kjournald starting.  Commit interval 5 seconds
[   51.764304] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   51.764580] EXT3 FS on sda6, internal journal
[   51.764586] EXT3-fs: mounted filesystem with ordered data mode.
flippo@flippo-server:~$


I should also note that I've tried to plug in a different externals, and none are getting a response, so I strongly believe its the computer, not the drive.  I'm going to thumb through my mobo manual quickly, do you have any other advice?

---

### Post by YesSir on 2009-02-04
I´m searching for a solution to the same problem and found these threads:

[http://ubuntuforums.org/showthread.php?t=857374&](http://ubuntuforums.org/showthread.php?t=857374&)
[http://ubuntuforums.org/showthread.php?t=1058970&](http://ubuntuforums.org/showthread.php?t=1058970&)

Maybe it´s helpful to you, I´m still looking for a solution ;)

---

