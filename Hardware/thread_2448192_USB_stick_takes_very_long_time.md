---
title: "USB stick takes very long time"
date: 2020-08-04
forum: Hardware
---

### Post by jenniferruurs on 2020-08-04
I have a very large USB stick (512GB) that does very long time to load compared to my other sticks (5minutes sometimes).

Does anybody have idea why this is, and how i can solve it?

Output of:
journalctl -f

```
aug 04 10:38:31  kernel: usb 4-6: new SuperSpeed USB device number 4 using xhci_hcd
aug 04 10:38:31  kernel: usb 4-6: New USB device found, idVendor=090c, idProduct=2000
aug 04 10:38:31  kernel: usb 4-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
aug 04 10:38:31  kernel: usb 4-6: Product: USB DISK01
aug 04 10:38:31  kernel: usb 4-6: Manufacturer: SMI Corporation01
aug 04 10:38:31  kernel: usb 4-6: SerialNumber: 04307003000039
aug 04 10:38:31  kernel: usb-storage 4-6:1.0: USB Mass Storage device detected
aug 04 10:38:31  kernel: scsi host5: usb-storage 4-6:1.0
aug 04 10:38:31  mtp-probe[3670]: checking bus 4, device 4: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-6"
aug 04 10:38:31  mtp-probe[3670]: bus: 4, device: 4 was not an MTP device
aug 04 10:38:33  kernel: scsi 5:0:0:0: Direct-Access     SMI01    USB DISK01       1100 PQ: 0 ANSI: 6
aug 04 10:38:33  kernel: sd 5:0:0:0: [sdb] 983040000 512-byte logical blocks: (503 GB/469 GiB)
aug 04 10:38:33  kernel: sd 5:0:0:0: [sdb] Write Protect is off
aug 04 10:38:33  kernel: sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
aug 04 10:38:33  kernel: sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
aug 04 10:38:33  kernel: sd 5:0:0:0: Attached scsi generic sg2 type 0
aug 04 10:38:33  kernel:  sdb: sdb1
aug 04 10:38:33  kernel: sd 5:0:0:0: [sdb] Attached SCSI removable disk
aug 04 10:47:04 kernel: INFO: task gnome-disks:3952 blocked for more than 120 seconds.
aug 04 10:47:04 kernel:       Tainted: G        W        4.15.0-112-generic #113~16.04.1-Ubuntu
aug 04 10:47:04 kernel: "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

```

---

### Post by TheFu on 2020-08-05
Use an internal, NVMe SSD for the install instead?

What do you mean, exactly, by "a very long time to load"? 

Is that boot, reading a directory, show billions of files in the same directory or something else?  Is it an OS or data storage device?

What speed is the port it is plugged into?  USB1, 1.1, 2.0, 3.0, 3.1, 4 or something faster?

Is there a USB hub involved?  Don't do that.

What file system does it have?  For the best performance on a USB flash drive, use f2fs, or ext4, if you don't care about lifespan.  FAT32 will be crazy slow for that size. exFAT might be slow for 18.04 and earlier versions. I know a bunch of work has been done to make exFAT faster the last few months, but doubt that has made it into any Linux updates anywhere - unless you pull the newest, alpha, kernels and drivers.

---

