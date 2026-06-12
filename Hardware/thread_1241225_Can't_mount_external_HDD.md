---
title: "Can't mount external HDD"
date: 2009-08-15
forum: Hardware
---

### Post by sideaway on 2009-08-15
For some reason I can't mount my Toshiba Gigabeat and use it's HDD. I have rockbox on it and would like to copy some music onto it.

Some information:

dmesg:
```
[93757.884493] usb 2-3: new high speed USB device using ehci_hcd and address 4
[93758.017146] usb 2-3: configuration #1 chosen from 1 choice
[93758.220335] Initializing USB Mass Storage driver...
[93758.220415] scsi8 : SCSI emulation for USB Mass Storage devices
[93758.220463] usb-storage: device found at 4
[93758.220465] usb-storage: waiting for device to settle before scanning
[93758.220470] usbcore: registered new interface driver usb-storage
[93758.220472] USB Mass Storage support registered.
[93915.295497] usb 2-3: USB disconnect, address 4
[93923.872011] usb 2-3: new high speed USB device using ehci_hcd and address 5
[93924.005768] usb 2-3: configuration #1 chosen from 1 choice
[93924.006008] scsi9 : SCSI emulation for USB Mass Storage devices
[93924.006288] usb-storage: device found at 5
[93924.006289] usb-storage: waiting for device to settle before scanning
[94081.973709] usb 2-3: USB disconnect, address 5
[133204.172013] usb 2-3: new high speed USB device using ehci_hcd and address 6
[133204.309764] usb 2-3: configuration #1 chosen from 1 choice
[133204.316511] scsi10 : SCSI emulation for USB Mass Storage devices
[133204.316653] usb-storage: device found at 6
[133204.316654] usb-storage: waiting for device to settle before scanning

```


lsusb:
```
Bus 002 Device 006: ID 0930:0009 Toshiba Corp. Gigabeat F/X (HDD audio player)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 0471:0815 Philips eHome Infrared Receiver
Bus 008 Device 002: ID 045e:0724 Microsoft Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

sudo fdisk -l
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a06df5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       12161    97683201    7  HPFS/NTFS
/dev/sda3           12162       23711    92775375   83  Linux
/dev/sda4           23712       24321     4899825    5  Extended
/dev/sda5           23712       24321     4899793+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d2020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00053e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976758784    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
63 heads, 30 sectors/track, 516811 cylinders
Units = cylinders of 1890 * 512 = 967680 bytes
Disk identifier: 0xdec957a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           2      516811   488384504    7  HPFS/NTFS

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fb2fcce

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdec957ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001    7  HPFS/NTFS

```

Anyone know why I can't mount it? I can't even see it anywhere in nautilus to begin. And I can't use the terminal because it doesn't get assigned a name like sdg* or something.

---

### Post by sideaway on 2009-08-15
*bump*

Cheers guys... :)

---

### Post by dabl on 2009-08-16
Is this the external drive?:

>    Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001    7  HPFS/NTFS

Try booting your Ubuntu system and after you're logged in and any scripts are done, plug in the usb connector for your Gigabeat.

Does the "device notifier" pop up?  If so, click on it and maybe you'll be able to use it.

---

### Post by shrimpy89 on 2009-08-18
I have the same problem.  My Rockbox'd Gigabeat F40 isn't recognized by Ubuntu, although the player knows it's been USB connected.  I have to switch to Vista to put new songs on.  Very upsetting, obviously :)

---

