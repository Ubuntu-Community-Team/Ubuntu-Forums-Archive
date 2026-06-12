---
title: "U3 USB pendrive partition problem"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by guille2306 on 2007-05-14
Hi, I have some problem with a Kinsgton DataTraveler U3. Writing to the "FAT" partition produces some times corrupted files, which can not be erased nor readed. The error is something like "this file is in a read-only media", even if I have just written to it! The only way to correct the error is to take the USB to a Windows machine and to make a *chkdsk /f* of the drive. In this case I obtain a lot of "bad link" and "orphan blocks" errors, all of them related to the corrupted files. After that, the USB drive works perfectly. I tried formatting the partition on Windows, but the error persist. I think the problem first appeared after I upgraded from 6.10 to 7.04, but I am not sure.

When I plug it, it is recognized correctly, this is the exit of *dmesg*:

```
[47841.368841] usb 4-4: new high speed USB device using ehci_hcd and address 2
[47841.501625] usb 4-4: configuration #1 chosen from 1 choice
[47841.991457] usbcore: registered new interface driver libusual
[47842.026830] Initializing USB Mass Storage driver...
[47842.026961] scsi0 : SCSI emulation for USB Mass Storage devices
[47842.027044] usbcore: registered new interface driver usb-storage
[47842.027048] USB Mass Storage support registered.
[47842.027269] usb-storage: device found at 2
[47842.027271] usb-storage: waiting for device to settle before scanning
[47847.022881] usb-storage: device scan complete
[47847.023521] scsi 0:0:0:0: Direct-Access     Kingston DataTraveler U3  6.16 PQ: 0 ANSI: 0 CCS
[47847.023979] scsi 0:0:0:1: CD-ROM            Kingston DataTraveler U3  6.16 PQ: 0 ANSI: 0
[47847.069294] SCSI device sda: 1996799 512-byte hdwr sectors (1022 MB)
[47847.070154] sda: Write Protect is off
[47847.070158] sda: Mode Sense: 45 00 00 08
[47847.070160] sda: assuming drive cache: write through
[47847.072151] SCSI device sda: 1996799 512-byte hdwr sectors (1022 MB)
[47847.072899] sda: Write Protect is off
[47847.072902] sda: Mode Sense: 45 00 00 08
[47847.072904] sda: assuming drive cache: write through
[47847.073100]  sda: sda1
[47847.074425] sd 0:0:0:0: Attached scsi removable disk sda
[47847.107354] sd 0:0:0:0: Attached scsi generic sg0 type 0
[47847.107797] scsi 0:0:0:1: Attached scsi generic sg1 type 5
[47847.240334] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[47847.240752] sr 0:0:0:1: Attached scsi CD-ROM sr0
```

I mount the device through the following *fstab* line

```
/dev/sda1	/media/usb	auto	rw,users,noauto	0	0
```

and after mounted the exit of *fdisk -l* is

```
Disk /dev/sda: 1022 MB, 1022361088 bytes
129 heads, 16 sectors/track, 967 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         968      998391+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(973, 128, 16) logical=(967, 56, 15)
```

I guess the problem comes from this "*different physical/logical endings*", but that is the farthest I can go... :-) Any ideas on how to solve it?

---

### Post by abelnieva on 2007-07-13
I have a same problem, with Pendrive Kingston 2Gb Data Travel :(

---

### Post by Licurgo on 2007-07-13
Have you tried the uninstall software?
Try this: [http://www.u3.com/support/#CQ3](http://www.u3.com/support/#CQ3)
I hope you solve the problem

---

### Post by guille2306 on 2007-07-14
> **Licurgo said:**
> Have you tried the uninstall software?
Try this: [http://www.u3.com/support/#CQ3](http://www.u3.com/support/#CQ3)
I hope you solve the problem

Well, that will uninstall the U3 system without recovery. Probably that will solve the problem (I don't know for sure), but that's something I don't want to do (I use this pendrive in linux and windows, and some times is useful to have the U3...)

---

### Post by abelnieva on 2007-07-15
$sudo fsck.vfat -y -f /dev/sda1 
formateando la unidad con ese comando, aparentemente se soluciona el problema. ya que no he tenido problemas por ahora.

---

### Post by guille2306 on 2007-08-31
> **abelnieva said:**
> $sudo fsck.vfat -y -f /dev/sda1 
formateando la unidad con ese comando, aparentemente se soluciona el problema. ya que no he tenido problemas por ahora.

Thanks for the command, is the Linux equivalent for chkdsk that I was looking for.

Besides that, I think I've found the problem. After a while of not seeing it, it appeared again yesterday but this time a know what I did. When you unmount an external drive, normally you have to wait some moments for the data that is still in the write cache of the system to actually write into it. But for some reason in Ubuntu it doesn't tell you that is doing that!!! Even if the drive appears as unmounted, there isn't a "You can safely remove the drive now" pop-up to confirm this, so you have to wait for the light of the pen-drive to stop blinking fast.

---

