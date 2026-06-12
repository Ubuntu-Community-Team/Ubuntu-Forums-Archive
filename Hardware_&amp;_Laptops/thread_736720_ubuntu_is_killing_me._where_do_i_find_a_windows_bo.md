---
title: "ubuntu is killing me. where do i find a windows boot disk?"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by nabiscOGrahams on 2008-03-26
ubuntu does not recognize my external hard drive im fed up..

where can i find a windows boot disk?

---

### Post by giants_fan on 2008-03-26
Is your external HD formatted NTFS?

If so, Ubuntu won't read it out-of-the-box.

---

### Post by nabiscOGrahams on 2008-03-27
ntfs? i dont know.. how do i check? how do i format it as such?

---

### Post by tubasoldier on 2008-03-27
It is more than likely NTFS. NTFS is the windows filesystem. You would have to install ntfs-3g to access it.


If you really want Windows back put your WinXP disk in the drive and boot from it. Thats the boot disk.

---

### Post by ellis rowell on 2008-03-27
You may have the same problem as I have.
I installed a second HDD as a secondary drive (Cable Select) it was formatted as Fat 32 (recognised by Ubuntu as VFat) but failed to mount on booting. I have to go into 'Places' then click 'Computer'. It appears listed as a drive, double click on the icon then enter your password (for root action) and it then mounts.

Give it a try. If this doesn't work, try going to your root directory and clicking on 'media' (it may show there).

---

### Post by PmDematagoda on 2008-03-27
You can get the second drive to be mounted at boot, all you need to do is to add the appropriate entry in the fstab file.

---

### Post by nabiscOGrahams on 2008-03-27
fstab file? i dont know what that means?

my comp does not recognize the drive anywhere.. not in root/media.. not in places/computer..

any other suggestions?

on another note... i have a Windows XP "Operating System CD" but my comp will not boot from it.. I understand how to boot from a disk but this disk simply does not work.. Is there anywhere online i can find a boot disk?

Thanks!

---

### Post by nabiscOGrahams on 2008-03-27
also.

```
pat@pat-laptop:~$ sudo apt-get install ntfs-3g
[sudo] password for pat:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by giants_fan on 2008-03-27
Is this an external USB drive?  When you plug it it, does it look like it tries to do anything?  Does the HD spin up at all?  

I still think the prob is that its NTFS.  Plug the drive into a Windows box and right click, properties on the drive icon and it should say how it's been formatted.

To answer your other question--computer won't boot from CD--my guess is that you need to go into your BIOS (how to actually do this is different from computer-to-computer) and tell it to boot from CD before booting from the hard disk.

---

### Post by nabiscOGrahams on 2008-03-27
Yes it is an external hard drive.

It is formatted FAT32.

When I plug it in, its light turns on.. It sounds like its spinning but no recognition by Ubuntu.

Please help me guys...

---

### Post by nabiscOGrahams on 2008-03-27
I just ran gparted.. 

The external hard drive is not listed anywhere.

---

### Post by BoA CoNsTrIcToR on 2008-03-28
Plug in your external drive and run 'sudo dmesg' to find out which device has the hard disk been detected as if you know the maker of the device. Else, first run 'lsusb' find out the maker and then run 'dmesg' to find the detection location.

I have been using an external USB HDD formatted to ext3 (earlier it was FAT32 but changed to store ISO images. FAT can't go beyond 4GB) and it has been working fine since the day of purchase.

I am just pasting a sample dmesg output that is generated when i plug my USB stick. Read the comments within [] in the output.

[INDENT][INDENT][ 1845.900688] usb 6-3: new high speed USB device using ehci_hcd and address 2
[ 1846.376039] usb 6-3: configuration #1 chosen from 1 choice
[ 1846.449769] usbcore: registered new interface driver libusual
[ 1846.461184] Initializing USB Mass Storage driver...
[ 1846.461294] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1846.461364] usb-storage: device found at 2
[ 1846.461369] usbcore: registered new interface driver usb-storage
[ 1846.461374] USB Mass Storage support registered.
[ 1846.461377] usb-storage: waiting for device to settle before scanning
[ 1851.448139] usb-storage: device scan complete
[ 1851.463597] scsi 4:0:0:0: Direct-Access     **JetFlash TS2GJFV30[\B][B]* [the maker] ***       8.07 PQ: 0 ANSI: 2
[ 1851.465692] SCSI device sdb: 4014078 512-byte hdwr sectors (2055 MB)
[ 1851.466313] sdb: Write Protect is off
[ 1851.466319] sdb: Mode Sense: 03 00 00 00
[ 1851.466324] sdb: assuming drive cache: write through
[ 1851.468433] SCSI device sdb: 4014078 512-byte hdwr sectors (2055 MB)
[ 1851.469055] sdb: Write Protect is off
[ 1851.469060] sdb: Mode Sense: 03 00 00 00
[ 1851.469065] sdb: assuming drive cache: write through
[ 1851.469068]  sdb: sdb1**---------------------------------------------------->[mount this drive]**
[ 1851.469755] sd 4:0:0:0: Attached scsi removable disk sdb
[ 1851.469811] sd 4:0:0:0: Attached scsi generic sg2 type 0[/INDENT][/INDENT]

---

