---
title: "Formatting Broken iPod and installing Linux on it"
date: 2011-07-09
forum: Hardware
---

### Post by Tom1989 on 2011-07-09
Please excuse me if the answer to my problem exists already but after spending ages trawling through forums I still can't solve things.

I have a knackered 4thGen iPod that I want to reformat and install Ubuntu on so I can plug it into computers and boot from it.

I will list all the things I have tried:

tom@ubuntu:~$ mount iPod
mount: can't find iPod in /etc/fstab or /etc/mtab

tom@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:1203 Apple, Inc. iPod 4.Gen Grayscale 40G
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

tom@ubuntu:~$ dmesg | tail
[  235.472199] Dev sdb: unable to read RDB block 0
[  235.472221] sd 6:0:0:0: rejecting I/O to offline device
[  235.472258] sd 6:0:0:0: rejecting I/O to offline device
[  235.472307] sd 6:0:0:0: rejecting I/O to offline device
[  235.472343] sd 6:0:0:0: rejecting I/O to offline device
[  235.472381] sd 6:0:0:0: rejecting I/O to offline device
[  235.472418] sd 6:0:0:0: rejecting I/O to offline device
[  235.472436]  unable to read partition table
[  235.472712] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 1540.603868] npviewer.bin[1782]: segfault at 418 ip 00000000f6093c86 sp 00000000ff87a448 error 6 in libflashplayer.so[f5e44000+b2e000]


The screen of my iPod claims it's in Disk mode but I can hear it trying to connect and failing. From the above commands it looks to me like Ubuntu is seeing my iPod but doesn't want to play with it. Also my iPod is 20g and not 40g as claimed by lsusb. 

Like I said I have tried everything I could find but I could really use some advice and help please.

Thank you all.

---

### Post by Tom1989 on 2011-07-09
Also, sorry for starting ANOTHER iPod thread!

---

### Post by Tom1989 on 2011-07-09
Update:

on closer inspection dmesg revealed this:


[    1.910760]  sda: sda1
[    1.963139] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.270467] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b240000f1055f]
[    3.321414] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    5.962840] usb-storage: device scan complete
[    5.963532] scsi 5:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0

---

### Post by Tom1989 on 2011-07-19
bump

---

