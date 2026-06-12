---
title: "Slow file transfer via USB 3.0 and high CPU load"
date: 2014-10-09
forum: Hardware
---

### Post by dec3 on 2014-10-09
Hi,

I experience a strange behaviour when copying files to my USB 3.0 thumb drives.

I wanted to install Windows 7 on another PC (not mine! ;) ). So I copied the files from the SSD (ext4) to the thumb drive after formatting it to NTFS. The first 600Mb are copied at high speed, just as expected. But then the rate drops below 1Mb/s which averages to 3.4Mb/s after finishing to copy all files (3470 files, 3.9Gb).
During copying, the CPU load rises to 100%, according to the cpu speed indicator. I can't identify an process consuming 100% cpu time using top. But the load average is above 3.5 and even audio playback starts stuttering.

I also copied the same files from another internal harddisk (no SSD, NTFS). That, at least, doubled the transfere rate. It's still slow, but better.

Summary:

File: "Win7" 3.9Gb
Source: NTFS HDD
Destination: Thumb drive, NTFS
Average speed: 7Mb/s

File: "Win7" 3.9Gb
Source: EXT4 SSD
Destination: Thumb drive, NTFS
Average speed: 3.5Mb/s

File: 6.9Gb tar
Source: NTFS HDD
Destination: Thumb drive, NTFS
Average speed: 20Mb/s

File: 6.9Gb tar
Source: EXT4 SSD
Destination: Thumb drive, NTFS
Average speed: 23Mb/s

File: 6.9Gb tar
Source: EXT4 SSD
Destination: Thumb drive, EXT4
Average speed: 20.5Mb/s

File: 6.9Gb tar
Source: NTFS HDD
Destination: Thumb drive, EXT4
Average speed: 21.4Mb/s

CPU load is always high, so it's not only NTFS related. I repeated the this with another thumb drive and it gave me approximately the same results.


Now that made me curious and I retried it with an external USB 3.0 HDD:

File: 6.9Gb tar
Source: NTFS HDD
Destination: USB 3.0 HDD, EXT4
Average speed: 82Mb/s

File: 6.9Gb tar
Source: EXT4 SSD
Destination: USB 3.0 HDD, EXT4
Average speed: 209Mb/s

Especially for the last test, the CPU load was lower. Before that I sometimes saw ntfs popping up in top (but only using a few % cpu).



Output in syslog when attaching thumb drive:
```
Oct  9 19:09:06 inspiron kernel: [ 1272.654415] usb 4-2: new SuperSpeed USB device number 4 using xhci_hcd
Oct  9 19:09:06 inspiron kernel: [ 1272.670876] usb 4-2: New USB device found, idVendor=0781, idProduct=5581
Oct  9 19:09:06 inspiron kernel: [ 1272.670884] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct  9 19:09:06 inspiron kernel: [ 1272.670887] usb 4-2: Product: Ultra
Oct  9 19:09:06 inspiron kernel: [ 1272.670890] usb 4-2: Manufacturer: SanDisk
Oct  9 19:09:06 inspiron kernel: [ 1272.670893] usb 4-2: SerialNumber: 4C530123250906103565
Oct  9 19:09:06 inspiron kernel: [ 1272.671745] usb-storage 4-2:1.0: USB Mass Storage device detected
Oct  9 19:09:06 inspiron kernel: [ 1272.672108] scsi9 : usb-storage 4-2:1.0
Oct  9 19:09:06 inspiron mtp-probe: checking bus 4, device 4: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-2"
Oct  9 19:09:06 inspiron mtp-probe: bus: 4, device: 4 was not an MTP device
Oct  9 19:09:07 inspiron kernel: [ 1273.671744] scsi 9:0:0:0: Direct-Access     SanDisk  Ultra            1.00 PQ: 0 ANSI: 6
Oct  9 19:09:07 inspiron kernel: [ 1273.672404] sd 9:0:0:0: Attached scsi generic sg3 type 0
Oct  9 19:09:07 inspiron kernel: [ 1273.672598] sd 9:0:0:0: [sdd] 62566488 512-byte logical blocks: (32.0 GB/29.8 GiB)
Oct  9 19:09:07 inspiron kernel: [ 1273.673468] sd 9:0:0:0: [sdd] Write Protect is off
Oct  9 19:09:07 inspiron kernel: [ 1273.673475] sd 9:0:0:0: [sdd] Mode Sense: 43 00 00 00
Oct  9 19:09:07 inspiron kernel: [ 1273.673882] sd 9:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Oct  9 19:09:07 inspiron kernel: [ 1273.712009]  sdd: sdd1
Oct  9 19:09:07 inspiron kernel: [ 1273.713298] sd 9:0:0:0: [sdd] Attached SCSI removable disk
Oct  9 19:09:07 inspiron ntfs-3g[5775]: Version 2013.1.13AR.1 external FUSE 29
Oct  9 19:09:07 inspiron ntfs-3g[5775]: Mounted /dev/sdd1 (Read-Write, label "SANDISK", NTFS 3.1)
Oct  9 19:09:07 inspiron ntfs-3g[5775]: Cmdline options: rw,nosuid,nodev,uhelper=udisks2,uid=1000,gid=1000,dmask=0077,fmask=0177
Oct  9 19:09:07 inspiron ntfs-3g[5775]: Mount options: rw,nosuid,nodev,uhelper=udisks2,allow_other,nonempty,relatime,default_permissions,fsname=/dev/sdd1,blkdev,blksize=4096
```


Any hint?

---

### Post by Michael_McKenney on 2014-10-09
USB creates transfer headers.  On smaller files, it can crawl.  USB 3 still has this problem that USB 1 and 2 had.  You could zip them up into one file and move it to get around it.  Then, unzip it on the other side.

---

### Post by dec3 on 2014-10-09
Maybe the overhead doesn't make it very efficient. But copying to the external HDD is very fast, even when I copy many small files. So that's not the problem here. I copyied almost the same "Win7" files from a windows machine to a thumb drive. There was no speed issue (>20Mb/s).

---

### Post by sudodus on 2014-10-10
Many pendrives alias thumb drives have slow flash memory, so that it will limit the transfer speed to lower values than possible with USB 2 or USB 3. If you select a fast drive according to tests, you can get ***much*** better performance than the average. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/") 
[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

