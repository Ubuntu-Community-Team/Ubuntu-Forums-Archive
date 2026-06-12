---
title: "[SOLVED] Help me mount this device"
date: 2008-09-24
forum: Hardware
---

### Post by MaindotC on 2008-09-24
I have this [imitation ipod called Super Talent](http://www.supertalent.com/products/mp3_detail.php?type=VIDEGO28%20MP4) that I got and I'd like to find a way to mount it.  I also have [this imitator called the iTalent](http://www.italentmp4.com/home/i51.php) that auto-mounts when I plug it in.  They both use what appears to be the same software and they're both manufactured by the same company.  It's by far the biggest bang for the buck that I've found in PMP's so far.

Anyway, when I connect the Super Talent it doesn't auto-mount so please help me figure out how to mount it.  Here are some outputs from when I plug it in that I hope you'll find informative:

/var/log/syslog
```

Sep 24 13:46:42 amd64-desktop kernel: [55374.672593] usb 5-5: new high speed USB device using ehci_hcd and address 11
Sep 24 13:46:42 amd64-desktop kernel: [55374.719181] usb 5-5: device descriptor read/64, error -71
Sep 24 13:46:43 amd64-desktop kernel: [55374.809033] usb 5-5: device descriptor read/64, error -71
Sep 24 13:46:43 amd64-desktop kernel: [55374.898884] usb 5-5: new high speed USB device using ehci_hcd and address 12
Sep 24 13:46:43 amd64-desktop kernel: [55374.954233] usb 5-5: configuration #1 chosen from 1 choice
Sep 24 13:46:43 amd64-desktop NetworkManager: <debug> [1222278403.388875] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55'). 
Sep 24 13:46:43 amd64-desktop kernel: [55374.970582] scsi8 : SCSI emulation for USB Mass Storage devices
Sep 24 13:46:43 amd64-desktop kernel: [55374.972388] usb-storage: device found at 12
Sep 24 13:46:43 amd64-desktop kernel: [55374.972392] usb-storage: waiting for device to settle before scanning
Sep 24 13:46:43 amd64-desktop NetworkManager: <debug> [1222278403.562084] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0'). 
Sep 24 13:46:48 amd64-desktop kernel: [55377.052066] usb-storage: device scan complete
Sep 24 13:46:48 amd64-desktop kernel: [55377.052374] scsi 8:0:0:0: Direct-Access     Company  PMP Platform OPN      PQ: 0 ANSI: 2
Sep 24 13:46:48 amd64-desktop kernel: [55377.052577] scsi 8:0:0:1: Direct-Access     Company  PMP Platform SDC      PQ: 0 ANSI: 2
Sep 24 13:46:48 amd64-desktop kernel: [55377.055582] sd 8:0:0:0: [sdc] 1010560 4096-byte hardware sectors (4139 MB)
Sep 24 13:46:48 amd64-desktop kernel: [55377.057048] sd 8:0:0:0: [sdc] Write Protect is off
Sep 24 13:46:48 amd64-desktop kernel: [55377.057050] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Sep 24 13:46:48 amd64-desktop kernel: [55377.057052] sd 8:0:0:0: [sdc] Assuming drive cache: write through
Sep 24 13:46:48 amd64-desktop kernel: [55377.057875] sd 8:0:0:0: [sdc] 1010560 4096-byte hardware sectors (4139 MB)
Sep 24 13:46:48 amd64-desktop kernel: [55377.058136] sd 8:0:0:0: [sdc] Write Protect is off
Sep 24 13:46:48 amd64-desktop kernel: [55377.058139] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Sep 24 13:46:48 amd64-desktop kernel: [55377.058140] sd 8:0:0:0: [sdc] Assuming drive cache: write through
Sep 24 13:46:48 amd64-desktop kernel: [55377.058143]  sdc: unknown partition table
Sep 24 13:46:48 amd64-desktop kernel: [55377.059819] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Sep 24 13:46:48 amd64-desktop kernel: [55377.059848] sd 8:0:0:0: Attached scsi generic sg3 type 0
Sep 24 13:46:48 amd64-desktop kernel: [55377.060449] sd 8:0:0:1: [sdd] Attached SCSI removable disk
Sep 24 13:46:48 amd64-desktop kernel: [55377.060470] sd 8:0:0:1: Attached scsi generic sg4 type 0
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.665997] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0_scsi_host'). 
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.676916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0_scsi_host_scsi_device_lun0'). 
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.785529] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.849811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0_scsi_host_scsi_device_lun1'). 
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.888452] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.996229] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Company_PMP_Platform_SDC_A55A55A55A55_0_1'). 
Sep 24 13:46:49 amd64-desktop NetworkManager: <debug> [1222278409.147533] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Company_PMP_Platform_OPN_A55A55A55A55_0_0').

```

/var/log/messges
```

Sep 24 13:46:42 amd64-desktop kernel: [55374.672593] usb 5-5: new high speed USB device using ehci_hcd and address 11
Sep 24 13:46:43 amd64-desktop kernel: [55374.898884] usb 5-5: new high speed USB device using ehci_hcd and address 12
Sep 24 13:46:43 amd64-desktop kernel: [55374.954233] usb 5-5: configuration #1 chosen from 1 choice
Sep 24 13:46:43 amd64-desktop kernel: [55374.970582] scsi8 : SCSI emulation for USB Mass Storage devices
Sep 24 13:46:48 amd64-desktop kernel: [55377.052374] scsi 8:0:0:0: Direct-Access     Company  PMP Platform OPN      PQ: 0 ANSI: 2
Sep 24 13:46:48 amd64-desktop kernel: [55377.052577] scsi 8:0:0:1: Direct-Access     Company  PMP Platform SDC      PQ: 0 ANSI: 2
Sep 24 13:46:48 amd64-desktop kernel: [55377.055582] sd 8:0:0:0: [sdc] 1010560 4096-byte hardware sectors (4139 MB)
Sep 24 13:46:48 amd64-desktop kernel: [55377.057048] sd 8:0:0:0: [sdc] Write Protect is off
Sep 24 13:46:48 amd64-desktop kernel: [55377.057875] sd 8:0:0:0: [sdc] 1010560 4096-byte hardware sectors (4139 MB)
Sep 24 13:46:48 amd64-desktop kernel: [55377.058136] sd 8:0:0:0: [sdc] Write Protect is off
Sep 24 13:46:48 amd64-desktop kernel: [55377.058143]  sdc: unknown partition table
Sep 24 13:46:48 amd64-desktop kernel: [55377.059819] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Sep 24 13:46:48 amd64-desktop kernel: [55377.059848] sd 8:0:0:0: Attached scsi generic sg3 type 0
Sep 24 13:46:48 amd64-desktop kernel: [55377.060449] sd 8:0:0:1: [sdd] Attached SCSI removable disk
Sep 24 13:46:48 amd64-desktop kernel: [55377.060470] sd 8:0:0:1: Attached scsi generic sg4 type 0

```

/var/log/kern.log
```

Sep 24 13:46:42 amd64-desktop kernel: [55374.672593] usb 5-5: new high speed USB device using ehci_hcd and address 11
Sep 24 13:46:42 amd64-desktop kernel: [55374.719181] usb 5-5: device descriptor read/64, error -71
Sep 24 13:46:43 amd64-desktop kernel: [55374.809033] usb 5-5: device descriptor read/64, error -71
Sep 24 13:46:43 amd64-desktop kernel: [55374.898884] usb 5-5: new high speed USB device using ehci_hcd and address 12
Sep 24 13:46:43 amd64-desktop kernel: [55374.954233] usb 5-5: configuration #1 chosen from 1 choice
Sep 24 13:46:43 amd64-desktop kernel: [55374.970582] scsi8 : SCSI emulation for USB Mass Storage devices
Sep 24 13:46:43 amd64-desktop kernel: [55374.972388] usb-storage: device found at 12
Sep 24 13:46:43 amd64-desktop kernel: [55374.972392] usb-storage: waiting for device to settle before scanning
Sep 24 13:46:48 amd64-desktop kernel: [55377.052066] usb-storage: device scan complete
Sep 24 13:46:48 amd64-desktop kernel: [55377.052374] scsi 8:0:0:0: Direct-Access     Company  PMP Platform OPN      PQ: 0 ANSI: 2
Sep 24 13:46:48 amd64-desktop kernel: [55377.052577] scsi 8:0:0:1: Direct-Access     Company  PMP Platform SDC      PQ: 0 ANSI: 2
Sep 24 13:46:48 amd64-desktop kernel: [55377.055582] sd 8:0:0:0: [sdc] 1010560 4096-byte hardware sectors (4139 MB)
Sep 24 13:46:48 amd64-desktop kernel: [55377.057048] sd 8:0:0:0: [sdc] Write Protect is off
Sep 24 13:46:48 amd64-desktop kernel: [55377.057050] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Sep 24 13:46:48 amd64-desktop kernel: [55377.057052] sd 8:0:0:0: [sdc] Assuming drive cache: write through
Sep 24 13:46:48 amd64-desktop kernel: [55377.057875] sd 8:0:0:0: [sdc] 1010560 4096-byte hardware sectors (4139 MB)
Sep 24 13:46:48 amd64-desktop kernel: [55377.058136] sd 8:0:0:0: [sdc] Write Protect is off
Sep 24 13:46:48 amd64-desktop kernel: [55377.058139] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Sep 24 13:46:48 amd64-desktop kernel: [55377.058140] sd 8:0:0:0: [sdc] Assuming drive cache: write through
Sep 24 13:46:48 amd64-desktop kernel: [55377.058143]  sdc: unknown partition table
Sep 24 13:46:48 amd64-desktop kernel: [55377.059819] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Sep 24 13:46:48 amd64-desktop kernel: [55377.059848] sd 8:0:0:0: Attached scsi generic sg3 type 0
Sep 24 13:46:48 amd64-desktop kernel: [55377.060449] sd 8:0:0:1: [sdd] Attached SCSI removable disk
Sep 24 13:46:48 amd64-desktop kernel: [55377.060470] sd 8:0:0:1: Attached scsi generic sg4 type 0

```

/var/log/debug
```

Sep 24 13:46:43 amd64-desktop NetworkManager: <debug> [1222278403.388875] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55'). 
Sep 24 13:46:43 amd64-desktop kernel: [55374.972388] usb-storage: device found at 12
Sep 24 13:46:43 amd64-desktop kernel: [55374.972392] usb-storage: waiting for device to settle before scanning
Sep 24 13:46:43 amd64-desktop NetworkManager: <debug> [1222278403.562084] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0'). 
Sep 24 13:46:48 amd64-desktop kernel: [55377.052066] usb-storage: device scan complete
Sep 24 13:46:48 amd64-desktop kernel: [55377.057050] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Sep 24 13:46:48 amd64-desktop kernel: [55377.058139] sd 8:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.665997] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0_scsi_host'). 
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.676916] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0_scsi_host_scsi_device_lun0'). 
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.785529] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.849811] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0_scsi_host_scsi_device_lun1'). 
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.888452] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_115e_3_A55A55A55A55_if0_scsi_host_scsi_device_lun1_scsi_generic'). 
Sep 24 13:46:48 amd64-desktop NetworkManager: <debug> [1222278408.996229] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Company_PMP_Platform_SDC_A55A55A55A55_0_1'). 
Sep 24 13:46:49 amd64-desktop NetworkManager: <debug> [1222278409.147533] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Company_PMP_Platform_OPN_A55A55A55A55_0_0'). 

```

I think some of this kind of repeats itself - sorry if it appears as spam.  Can someone help me determine how to mount this?  Thanks!

---

### Post by MaindotC on 2008-09-25
I copied the /dev directory before (dev.txt) and after (dev1.txt) I added the device.  Here's the difference:

```

amd64@amd64-desktop:~/Desktop$ cmp dev.txt dev1.txt 
dev.txt dev1.txt differ: byte 3561, line 57

```

Here are lines 57 from both files - now that I think of it I'm not sure I should include any of the lines before or after but check it out and tell me if this helps:

```

ptyac	   ptyq6  ptyw0  sdc	     ttya8  ttyq2  ttyv8  usbdev5.3_ep04

ptyac	   ptyq6  ptyw0  sdd	     ttya8  ttyq2  ttyv8  usbdev5.3_ep04

```

What is sdd versus sdc?  SDD = solid disk drive?

---

### Post by eggdeng on 2008-09-25
Storage devices are labelled sda, sdb, sdc etc. If you have just one HDD, it will be called sda. If you plug in a usb device, it will be called sdb, the next one sdc and so on.
To mount the device manually, first create a directory to mount it to, eg
```
sudo mkdir /media/usbplayer
```
To make sure of the drive label, plug in the device and (quickly) run
```
dmesg | tail
```
Assuming it is labelled sdc, mount the first partition on the usb device to the folder you created
```
sudo mount /sdc1 /media/usbplayer
```

---

### Post by MaindotC on 2008-09-25
Hi, eggdeng.  Thanks for your advice.  I did a dmesg | tail and here's the output:

```

[117261.136341] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[117261.137168] sd 10:0:0:0: [sdc] 1010560 4096-byte hardware sectors (4139 MB)
[117261.137397] sd 10:0:0:0: [sdc] Write Protect is off
[117261.137399] sd 10:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[117261.137400] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[117261.137403]  sdc: unknown partition table
[117261.139134] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[117261.139161] sd 10:0:0:0: Attached scsi generic sg3 type 0
[117261.139658] sd 10:0:0:1: [sdd] Attached SCSI removable disk
[117261.139681] sd 10:0:0:1: Attached scsi generic sg4 type 0

```

I'm assuming that the drive is labeled sdd.  I tried the command you specified but there is no /sdd directory so I assumed you meant:
```

amd64@amd64-desktop:~$ sudo mount /dev/sdc /media/usbplayer/
mount: you must specify the filesystem type
[code]

Did you mean /dev/sdd ?

Someone in #ubuntuforums also suggested I can get some info with *sudo fdisk -l*:
[code]
Disk /dev/sdc: 4139 MB, 4139253760 bytes
128 heads, 62 sectors/track, 127 cylinders
Units = cylinders of 7936 * 4096 = 32505856 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
amd64@amd64-desktop:~$

```

---

### Post by eggdeng on 2008-09-26
```
sudo mount /dev/sdc /media/usbplayer/
```
Should be ```
/dev/sdc1
``` (You mount a partition, not a device). If it doesn't work, try ```
/dev/sdd1
```
I don't know if it will work as the system seems to be seeing the player as 2 separate disks and doesn't seem to be able to read the partition table.

---

### Post by MaindotC on 2008-09-26
It's still not working :(  I guess because it can't read the partition table then it can't read sdc1 which should be within sdc.  Is there any way to add filesystems to my machine so it has a broader ability to mount?  For example, I assume at some point Linux could not mount ntfs filesystems, but as it evolved it started to include support for ntfs so the machine would be able to read it.  How can I see what filesystems my machine can already read?  It's probably in fdisk - i'll man page it.

Thanks egg :)

---

### Post by MaindotC on 2008-09-26
DUDE, I GOT IT!!!  It's msdos filesystem ?!?!!?

```

amd64@amd64-desktop:/media$ sudo mount /dev/sdc /media/usbplayer/ -t msdos
amd64@amd64-desktop:/media$ ls usbplayer/
audio/ ebook/ image/ video/ 
amd64@amd64-desktop:/media$ cd usbplayer/
amd64@amd64-desktop:/media/usbplayer$ ls
audio  ebook  image  video
amd64@amd64-desktop:/media/usbplayer$ cd audio/
amd64@amd64-desktop:/media/usbplayer/audio$ ls
alt  hotelc~1.lrc  hotelc~1.wma  record  yester~1.lrc  yester~1.mp3

```

Egg you get a star for pointing me in the right direction.  Now how do I set my machine so everytime I attach this device it will automount it as msdos fs?

---

