---
title: "usb extdisk mount to same point every time?"
date: 2008-09-12
forum: General Help
---

### Post by takayuki on 2008-09-12
Hi,

How can I force my external usb hard disk to mount at the same point every time?

Usually, it mounts to /media/disk/.  But if I've got a usb stick plugged in, the usb hard disk will mount to /media/disk-1/

I've stared at the "how to fstab" page to no avail.

any help greatly appreciated.



here's my disk details:
```
bubox@sotec:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=83edfaf1-f3e0-4363-85f9-e975ce6317b7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=445f622b-5062-45a7-ae53-d0a1499c9fc6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
bubox@sotec:~$ sudo fdisk -l
Password:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30166   242308363+  83  Linux
/dev/hda2           30167       30401     1887637+   5  Extended
/dev/hda5           30167       30401     1887606   82  Linux swap / Solaris

Disk /dev/sda: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2431    19526976    b  W95 FAT32
bubox@sotec:~$ ls /dev/disk/* -lah
/dev/disk/by-id:
total 0
drwxr-xr-x 2 root root 160 2008-09-13 10:26 .
drwxr-xr-x 5 root root 100 2008-09-12 23:32 ..
lrwxrwxrwx 1 root root   9 2008-09-10 21:36 ata-ST3250620A_9QE0941X -> ../../hda
lrwxrwxrwx 1 root root  10 2008-09-10 21:36 ata-ST3250620A_9QE0941X-part1 -> ../../hda1
lrwxrwxrwx 1 root root  10 2008-09-10 21:36 ata-ST3250620A_9QE0941X-part2 -> ../../hda2
lrwxrwxrwx 1 root root  10 2008-09-10 21:36 ata-ST3250620A_9QE0941X-part5 -> ../../hda5
lrwxrwxrwx 1 root root   9 2008-09-13 10:26 usb-Myson_Century,_Inc._USB_Mass_Storage_Device_100 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-13 10:26 usb-Myson_Century,_Inc._USB_Mass_Storage_Device_100-part1 -> ../../sda1

/dev/disk/by-path:
total 0
drwxr-xr-x 2 root root 180 2008-09-13 10:26 .
drwxr-xr-x 5 root root 100 2008-09-12 23:32 ..
lrwxrwxrwx 1 root root   9 2008-09-13 10:26 pci-0000:00:10.2-usb-0:1:1.0-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root  10 2008-09-13 10:26 pci-0000:00:10.2-usb-0:1:1.0-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root   9 2008-09-10 21:36 pci-0000:00:11.1-ide-0:0 -> ../../hda
lrwxrwxrwx 1 root root  10 2008-09-10 21:36 pci-0000:00:11.1-ide-0:0-part1 -> ../../hda1
lrwxrwxrwx 1 root root  10 2008-09-10 21:36 pci-0000:00:11.1-ide-0:0-part2 -> ../../hda2
lrwxrwxrwx 1 root root  10 2008-09-10 21:36 pci-0000:00:11.1-ide-0:0-part5 -> ../../hda5
lrwxrwxrwx 1 root root   9 2008-09-10 21:36 pci-0000:00:11.1-ide-1:0 -> ../../hdc

/dev/disk/by-uuid:
total 0
drwxr-xr-x 2 root root 100 2008-09-13 10:26 .
drwxr-xr-x 5 root root 100 2008-09-12 23:32 ..
lrwxrwxrwx 1 root root  10 2008-09-10 21:36 445f622b-5062-45a7-ae53-d0a1499c9fc6 -> ../../hda5
lrwxrwxrwx 1 root root  10 2008-09-13 10:26 4890-108E -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-09-10 21:36 83edfaf1-f3e0-4363-85f9-e975ce6317b7 -> ../../hda1
bubox@sotec:~$ 

```

---

### Post by Pelham123 on 2008-09-13
Have a look here for making a permanent mount point for the drive..

[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-05/msg02837.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-05/msg02837.html)

And then take a look here for editing fstab..

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

The only problem with the second link is that it is a little dated - i.e. /dev/* is now replaced by UUID in fstab - but its a good thread for understanding the fstab 'file' and configuration choices

Good luck

---

### Post by takayuki on 2008-09-13
Pelham,

thanks for the reply.  i'll check out the links.

is making a permanent mount point standard procedure or something most don't do?

it really helps when making rsync backup scripts to have a permanent name for the external drive.

---

### Post by Herman on 2008-09-13
Another way is to give the file system in the USB drive a label. [Make a label for your ext3 file system]("http://users.bigpond.net.au/hermanzone/p10.htm#ext3_usbdisk_labelling")
[FAT32 usbdisk volume label]("http://users.bigpond.net.au/hermanzone/p10.htm#fat32_usbdisk_volume_label")

The name of the mount point that Ubuntu will make in /media for the USB disk will be it's file system label.

---

### Post by HRR on 2009-11-26
> **Herman said:**
> Another way is to give the file system in the USB drive a label.

Hi,
I find that after labeling the USB Drive say for example.. "USB_Drive1", that after each system reset, the USB drive is mounted as "USB_Drive1_".    
So, after reset, an "_" is added to the name so you get an additional "_" appended to the name after each successive system restart. 

A more permanent means of fixing the mount point needs to be used to be able to use this as a backup method.
[Ubuntu 9.10 system]

Thanks.

---

### Post by QLee on 2009-11-26
> **HRR said:**
> Hi,
I find that after labeling the USB Drive say for example.. "USB_Drive1", that after each system reset, the USB drive is mounted as "USB_Drive1_".    
So, after reset, an "_" is added to the name so you get an additional "_" appended to the name after each successive system restart. 

A more permanent means of fixing the mount point needs to be used to be able to use this as a backup method.
[Ubuntu 9.10 system]

Thanks.

When you gave the partition (drive) a label, did you use a "/" character as a character in the label (name)? ...or some other character that is not legal in a folder name?

I do something similar as what you say you want for some of my backup, and mounting by label works on my external USB drive. A small difference is, I don't mount it automatically, just manually when I need to use it.

If mounting by label doesn't suit you, the UUID of the drive will be unique, not likely any other partitions on your system have the same UUID unless you cloned the partition with dd or something, you could mount that way.

And, you can investigate "udev rules" which can be done to always give the device the same device node.

---

