---
title: "After doing the Upgrade to Karmic: Problem Mounting external USB media"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by saschi on 2009-11-04
Hey. Altough this is my first post on the Ubuntu forums I have been using this great OS for more than a year now. To only have Windows running under VBox for whenever I have no chance to avoid it and use the best alternative Desktop OS there is must have been the single best choice I ever made. 
Whenever I had to solve a problem using Ubuntu I quickly found a solution on the web.
This one however seems to be uncovered so far:

After doing the upgrade from jaunty to Karmic I have problems attaching various USB devices. My USB pen drive is being mounted correctly without any problems. But neither my photo camera nor my Ipod (5G 80GiB) are beinmg mounted automatically. I am forced to manually mount at the time. Has anyone experienced the same problem? How can this be solved. 
In case anyone is interested in it I have attached the syslog output after connecting my IPod.

Thanks for your kind help.


> Nov  4 22:15:33 sascha kernel: [26352.145456] hub 2-0:1.0: unable to enumerate USB device on port 2
Nov  4 22:15:37 sascha kernel: [26356.055872] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1e:8c:c5:f9:45:08:00 SRC=141.30.228.35 DST=141.30.228.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=8447 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov  4 22:15:42 sascha kernel: [26361.076144] usb 2-2: new high speed USB device using ehci_hcd and address 19
Nov  4 22:15:42 sascha kernel: [26361.219080] usb 2-2: configuration #1 chosen from 2 choices
Nov  4 22:15:42 sascha kernel: [26361.223951] scsi10 : SCSI emulation for USB Mass Storage devices
Nov  4 22:15:42 sascha kernel: [26361.224178] usb-storage: device found at 19
Nov  4 22:15:42 sascha kernel: [26361.224181] usb-storage: waiting for device to settle before scanning
Nov  4 22:15:47 sascha kernel: [26366.224366] usb-storage: device scan complete
Nov  4 22:15:47 sascha kernel: [26366.278502] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
Nov  4 22:15:47 sascha kernel: [26366.279559] sd 10:0:0:0: Attached scsi generic sg3 type 0
Nov  4 22:15:47 sascha kernel: [26366.288716] sd 10:0:0:0: [sdc] 39075372 2048-byte logical blocks: (80.0 GB/74.5 GiB)
Nov  4 22:15:47 sascha kernel: [26366.289823] sd 10:0:0:0: [sdc] Write Protect is off
Nov  4 22:15:47 sascha kernel: [26366.289831] sd 10:0:0:0: [sdc] Mode Sense: 68 00 00 08
Nov  4 22:15:47 sascha kernel: [26366.289837] sd 10:0:0:0: [sdc] Assuming drive cache: write through
Nov  4 22:15:47 sascha kernel: [26366.296489] sd 10:0:0:0: [sdc] 39075372 2048-byte logical blocks: (80.0 GB/74.5 GiB)
Nov  4 22:15:47 sascha kernel: [26366.298213] sd 10:0:0:0: [sdc] Assuming drive cache: write through
Nov  4 22:15:47 sascha kernel: [26366.298228]  sdc: sdc1 sdc2
Nov  4 22:15:47 sascha kernel: [26366.479589] sd 10:0:0:0: [sdc] 39075372 2048-byte logical blocks: (80.0 GB/74.5 GiB)
Nov  4 22:15:47 sascha kernel: [26366.480967] sd 10:0:0:0: [sdc] Assuming drive cache: write through
Nov  4 22:15:47 sascha kernel: [26366.480978] sd 10:0:0:0: [sdc] Attached SCSI removable disk

---

