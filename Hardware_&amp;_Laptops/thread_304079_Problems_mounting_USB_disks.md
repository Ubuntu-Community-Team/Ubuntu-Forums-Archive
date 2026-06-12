---
title: "Problems mounting USB disks"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by ltorgo on 2006-11-21
I'm unable to mount USB disks (I've tried two: a pen disk and an USB hard disk) on my 6.10 Edgy. The same disks work perfectly on my Centrino laptop with the same Ubuntu distribution and also under Windows, which make me think that this is not a problem on the side of the disks...

My system is a AMD64 3800+
$> uname -a 
Linux xxx 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux


When I try to check /var/log/messages while plugging in the USB pen I get the following:

Nov 21 15:17:42 localhost kernel: [1318257.210066] usb 2-5: new high speed USB device using ehci_hcd and address 2
Nov 21 15:17:42 localhost kernel: [1318257.347108] usb 2-5: configuration #1 chosen from 1 choice
Nov 21 15:17:43 localhost kernel: [1318258.616450] usbcore: registered new driver libusual
Nov 21 15:17:43 localhost kernel: [1318259.492803] Initializing USB Mass Storage driver...
Nov 21 15:17:43 localhost kernel: [1318259.492894] scsi4 : SCSI emulation for USB Mass Storage devices
Nov 21 15:17:43 localhost kernel: [1318259.492961] usbcore: registered new driver usb-storage
Nov 21 15:17:43 localhost kernel: [1318259.492965] USB Mass Storage support registered.
Nov 21 15:17:48 localhost kernel: [1318263.655493]   Vendor: USB 2.0   Model: Mobile Disk       Rev: 2.00
Nov 21 15:17:48 localhost kernel: [1318263.655513]   Type:   Direct-Access                      ANSI SCSI revision: 02
Nov 21 15:17:49 localhost kernel: [1318265.619693] ready
Nov 21 15:17:49 localhost kernel: [1318265.622427] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
Nov 21 15:17:49 localhost kernel: [1318265.623879] sdb: Write Protect is off
Nov 21 15:17:49 localhost kernel: [1318264.804101] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
Nov 21 15:17:49 localhost kernel: [1318264.805721] sdb: Write Protect is off
Nov 21 15:17:49 localhost kernel: [1318264.805731]  sdb: sdb1
Nov 21 15:17:49 localhost kernel: [1318264.807926] sd 4:0:0:0: Attached scsi removable disk sdb
Nov 21 15:17:49 localhost kernel: [1318264.807978] sd 4:0:0:0: Attached scsi generic sg1 type 0
Nov 21 15:17:49 localhost kernel: [1318265.060282] usb 2-5: reset high speed USB device using ehci_hcd and address 2
Nov 21 15:17:50 localhost kernel: [1318265.304096] usb 2-5: reset high speed USB device using ehci_hcd and address 2
Nov 21 15:17:50 localhost kernel: [1318265.547924] usb 2-5: reset high speed USB device using ehci_hcd and address 2
Nov 21 15:17:50 localhost kernel: [1318265.793669] usb 2-5: reset high speed USB device using ehci_hcd and address 2
Nov 21 15:17:50 localhost kernel: [1318266.039562] usb 2-5: reset high speed USB device using ehci_hcd and address 2
Nov 21 15:17:51 localhost kernel: [1318266.283379] usb 2-5: reset high speed USB device using ehci_hcd and address 2
Nov 21 15:17:51 localhost kernel: [1318266.415961] sd 4:0:0:0: SCSI error: return code = 0x70000
Nov 21 15:17:51 localhost kernel: [1318266.415966] end_request: I/O error, dev sdb, sector 511264


and then goes on repeating this same messages...

fdisk -l produces:
root@piela:~# fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        3648    19535040   83  Linux
/dev/sda3            3649        4256     4883760   82  Linux swap / Solaris
/dev/sda4            4257       10011    46227037+   5  Extended
/dev/sda5            4257        6080    14651248+  83  Linux
/dev/sda6            6081        7296     9767488+  83  Linux
/dev/sda7            7297        9120    14651248+  83  Linux
/dev/sda8            9121       10011     7156926   83  Linux

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12159    97667136   83  Linux
/dev/hda2           12160       14593    19551105   83  Linux

Disk /dev/sdb: 262 MB, 262144000 bytes
16 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         999      255728    b  W95 FAT32

so apparently the USB pen is on /dev/sdb1 ...

On Nautilus I get two "links" under Places saying:
"USB 2.0 Mobile Disk" and "USB Drive"
When I click on any of these I get a message box saying:
Unable to mount selected volume
mount:/dev/sdb1: can't read superblock

I do not get any icon on my desktop.

Any help would be very appretiated as I realy need to use these disks...

Thanks in advance,
Luis

---

### Post by taurus on 2006-11-21
Open a terminal, Applicatioons -> Accessories -> Terminal, and mount it by hand!!!

```
sudo mkdir /media/usb
sudo mount -t vfat /dev/sdb1 /media/usb
```

---

### Post by ltorgo on 2006-11-21
I've tried that but the mount command apparently never ends...

In between I've checked tail -f /var/log/messages and the log was being constantly filled in with messages like:

Nov 21 17:12:41 localhost kernel: [1325151.062531] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:41 localhost kernel: [1325151.306348] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:41 localhost kernel: [1325151.550198] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:41 localhost kernel: [1325152.677030] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:42 localhost kernel: [1325152.041812] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:42 localhost kernel: [1325152.337595] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:42 localhost kernel: [1325152.585440] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:42 localhost kernel: [1325152.833244] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:43 localhost kernel: [1325153.086421] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:43 localhost kernel: [1325153.336867] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:43 localhost kernel: [1325153.580678] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:43 localhost kernel: [1325153.824506] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:44 localhost kernel: [1325154.068319] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:44 localhost kernel: [1325154.312132] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:44 localhost kernel: [1325154.555936] usb 2-5: reset high speed USB device using ehci_hcd and address 3
Nov 21 17:12:44 localhost kernel: [1325154.688745] sd 5:0:0:0: SCSI error: return code = 0x70000
Nov 21 17:12:44 localhost kernel: [1325154.688751] end_request: I/O error, dev sdb, sector 478536

and so on only varying the sector number.

Finally, I've Ctrl-C'ed the mount command, but the messages continued to appear in the log...

Surprinsingly in the end a Nautilus Window appeared with the contents of the USB disk... but if I click on a folder in the disk, another flood of messages on the log and so on everytime I change folder...

After a few clicks it stoped working at all... :-(

In any case this (all the error messages and even the manual mount), does not seem a very healthy ;-) way to do it... Not that I mind the manual mount (if it fully worked and if it did not filled my logs with tons of messages). Still, there must be a "normal" plugin (like the one I do on my laptop) without all these problems, or is this an architecture dependent problem no yet solved?

Thanks for the help anyway.

Luis

---

