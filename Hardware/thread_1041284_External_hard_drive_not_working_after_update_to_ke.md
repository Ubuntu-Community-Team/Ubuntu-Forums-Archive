---
title: "External hard drive not working after update to kernel 2.6.27-11"
date: 2009-01-16
forum: Hardware
---

### Post by ELWisty on 2009-01-16
Hi,

Sorry if this has been asked before. I tried googling and searching the forums as well but could not find a thread exactly matching my problem.

Ok, the problem is following. Apologies if I have omitted some essential information. I'm very new to . Linux as I just recently switched over from Windows XP.

I have Ubuntu 8.10 (Intrepid) installed on an Acer Aspire 5040 laptop (replacing Windows XP). I've a 250 gb external LaCie hard drive. Earlier I had no problem with it, auto-mount worked ok etc. But after I updated to kernel version 2.6.27-11 this is history: the drive is powered up and connected, the light on, but it does not auto-mount, and it's not visible in the "Places" menu nor as an icon on desktop. I tried going back to 2.6.27-10 but no result. Also, no change trying different USB ports. Incidentally, also my Canon EOS 450D stopped auto-mounting, although it is recognized by F-Spot if I have the camera connected and the picture preview function on.

Results for the hard drive:

[B]
1) sudo fdisk -l:[/B]

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11832    95040508+  83  Linux
/dev/sda2           11833       12161     2642692+   5  Extended
/dev/sda5           11833       12161     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x454c3879

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32
[B]
2) lsusb:[/B]

Bus 003 Device 003: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 041e:3040 Creative Technology, Ltd SoundBlaster Live! 24-bit External SB0490
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 059f:0c41 LaCie, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**3) dmesg:**

[12623.212024] usb 1-3: new high speed USB device using ehci_hcd and address 7
[12623.363037] usb 1-3: configuration #1 chosen from 1 choice
[12623.405047] scsi3 : SCSI emulation for USB Mass Storage devices
[12623.416046] usb-storage: device found at 7
[12623.416052] usb-storage: waiting for device to settle before scanning
[12628.416963] usb-storage: device scan complete
[12628.485333] scsi 3:0:0:0: Direct-Access     TOSHIBA  MK2546GSX             PQ: 0 ANSI: 2 CCS
[12628.537677] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[12628.538422] sd 3:0:0:0: [sdb] Write Protect is off
[12628.538426] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[12628.538429] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[12628.539543] sd 3:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[12628.540173] sd 3:0:0:0: [sdb] Write Protect is off
[12628.540177] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[12628.540180] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[12628.540575]  sdb: sdb1
[12628.545052] sd 3:0:0:0: [sdb] Attached SCSI disk
[12628.545361] sd 3:0:0:0: Attached scsi generic sg2 type 0

****

Any help greatly appreciated.

---

### Post by taurus on 2009-01-16
See if you can mount it from a terminal.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by ELWisty on 2009-01-16
That did the trick! Thanks so much for the lightning-speed response!

Regards,

ELWisty

---

