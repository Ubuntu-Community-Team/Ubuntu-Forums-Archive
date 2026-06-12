---
title: "Not able to detect pen drive, cd, hard disk in ubuntu 12.10"
date: 2013-06-09
forum: Hardware
---

### Post by Akhilkumars on 2013-06-09
Hi ,

I am not able to detect any usb device or cd drive in ubuntu 12.10. I am completely novice ti ubuntu.
From some thread available, I tried mount /media/cdrom. But I got "  mount: can't find /media/cdrom/ in /etc/fstab or /etc/mtab "
Could someone help me :
[B]
The output of lsusb  with a pen drive pulggged is:[/B]

Bus 001 Device 002: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 002 Device 010: ID 8564:1000  
Bus 007 Device 005: ID 192f:0416 Avago Technologies, Pte. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

[B]Here, Bus 002 Device 010: ID 8564:1000  is the pen drive one.
[/B]
[B]The output of sudo fdisk -l :
[/B]
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001371b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   618930175   309464064   83  Linux
/dev/sda2       618932222   625141759     3104769    5  Extended
/dev/sda5       618932224   625141759     3104768   82  Linux swap / Solaris


Disk /dev/sdb: 4015 MB, 4015718400 bytes
80 heads, 15 sectors/track, 6536 cylinders, total 7843200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             256     7843199     3921472    b  W95 FAT32




Could someone please help me. Since urgently need to back up my files.

Thanks

---

### Post by Mark Phelps on 2013-06-09
If your CD-ROM is an internal drive, it will show up under "lspci" since it's not then connected through the USB bus.

You also shouldn't have to mount it manually.  When you stick a CD in it, you should see something on your desktop.

As to not seeing the pendrive, what is: > Bus 007 Device 005: ID 192f:0416 Avago Technologies, Pte. 

---

### Post by Akhilkumars on 2013-06-10
Hi Mark,

Unfortunately, I am not able to view the CD on the Desktop or in the side panel under devices.

[COLOR=#000000][I]Bus 007 Device 005: ID 192f:0416 Avago Technologies, Pte.  -----   

This is nothing but the USB mouse.

Thank[/I][/COLOR]

---

### Post by sudodus on 2013-06-10
Welcome to the Ubuntu Forums :-)

```
Disk /dev/sdb: 4015 MB, 4015718400 bytes
80 heads, 15 sectors/track, 6536 cylinders, total 7843200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             256     7843199     3921472    b  W95 FAT32
```

I think this is your USB drive. Try to mount it with the file browser (Click on it's icon in the left panel)

You can get more identification running

```
sudo blkid
```
and
```
sudo parted -l
```

and posting the output between code tags (mark and click on the # icon at the top of the editing window, or do it manually

[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

---

### Post by Akhilkumars on 2013-06-11
[COLOR=#000000]```
Testing
```

[/COLOR]

---

### Post by Akhilkumars on 2013-06-11
[FONT=Verdana]Hi,[/FONT]

[FONT=Verdana]I found that my DVD had some issues. So had to change it. Resolved !![/FONT]
[FONT=Verdana]The pen drive is detected.[/FONT]

[FONT=Verdana]Thanks[/FONT]

---

