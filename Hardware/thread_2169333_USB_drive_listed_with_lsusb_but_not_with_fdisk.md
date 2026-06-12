---
title: "USB drive listed with lsusb but not with fdisk"
date: 2013-08-21
forum: Hardware
---

### Post by PABlanche on 2013-08-21
OK, there is tones of posts describing a similar problem out there, I read them, but it did not solve my isuue.

My USB thump drive that use to work fine can not be mounted anymore
It is listed with "lsusb"
Bus 002 Device 006: ID 4146:9281 USBest Technology Iomega Micro Mini 128MB Flash Drive

However, it is not in the list of " fdisk -l". Only /dev/sda, no sdb. so I can not manually mount the disk.

I tryed the well known "modprobe usb_storage". That did not help, neither restarting with or without the thumbdrive inserted.

This thumpdrive can be mounted on other computers.
Another thump drive is auto mounting correctly on the computer (msdos file system type)

Any clue?

My system: Ubuntu 13.04, 64 bits up to date. The issue started after the last update (coincidental?)

Thanks,
-- 
PAB

---

### Post by VMC on 2013-08-21
Look at the "/var/log/syslog" for the usb device in question. What is your kernel version "uname -r". Also try leaving the usb in for at least 5 minutes and see if it gets mounted.

---

### Post by PABlanche on 2013-08-21
> **VMC said:**
> Look at the "/var/log/syslog" for the usb device in question. 

kernel: [15218.948613] usb 2-1.2: new high-speed USB device number 9 using ehci-pci
Aug 21 15:26:03 Pierre-EliteBook kernel: [15219.060282] usb 2-1.2: New USB device found, idVendor=4146, idProduct=9281
Aug 21 15:26:03 Pierre-EliteBook kernel: [15219.060289] usb 2-1.2: New USB device strings: Mfr=0, Product=1, SerialNumber=2
Aug 21 15:26:03 Pierre-EliteBook kernel: [15219.060293] usb 2-1.2: Product: I0MEGA
Aug 21 15:26:03 Pierre-EliteBook kernel: [15219.060297] usb 2-1.2: SerialNumber: 12345111510000000760
Aug 21 15:26:03 Pierre-EliteBook kernel: [15219.061193] scsi14 : usb-storage 2-1.2:1.0
Aug 21 15:26:03 Pierre-EliteBook mtp-probe: checking bus 2, device 9: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
Aug 21 15:26:03 Pierre-EliteBook mtp-probe: bus: 2, device: 9 was not an MTP device
Aug 21 15:26:04 Pierre-EliteBook kernel: [15220.202647] scsi 14:0:0:0: Direct-Access     I0MEGA   UMni256MB*IOM2E4 2.00 PQ: 0 ANSI: 0 CCS
Aug 21 15:26:04 Pierre-EliteBook kernel: [15220.204100] sd 14:0:0:0: Attached scsi generic sg2 type 0
Aug 21 15:26:04 Pierre-EliteBook kernel: [15220.205209] sd 14:0:0:0: [sdb] 501760 512-byte logical blocks: (256 MB/245 MiB)
Aug 21 15:26:04 Pierre-EliteBook kernel: [15220.205793] sd 14:0:0:0: [sdb] Write Protect is off
Aug 21 15:26:04 Pierre-EliteBook kernel: [15220.205799] sd 14:0:0:0: [sdb] Mode Sense: 00 06 00 00
Aug 21 15:26:04 Pierre-EliteBook kernel: [15220.206640] sd 14:0:0:0: [sdb] No Caching mode page present
Aug 21 15:26:04 Pierre-EliteBook kernel: [15220.206644] sd 14:0:0:0: [sdb] Assuming drive cache: write through

Foreign language to me

> **VMC said:**
>  What is your kernel version "uname -r". 

3.8.0-29-generic

> **VMC said:**
> 
Also try leaving the usb in for at least 5 minutes and see if it gets mounted.

Nope :(

---

### Post by VMC on 2013-08-21
You may be suffering from what I reported on a week or so ago. At the time , I was using 3.8.0-28. The fix is on the stable 3.10.7 kernel. Also on the Saucy kernels which is above that.

If its the LTS that your using, the only two solutions it to compile the kernel yourself and add the patch (a long process), or install a newer kernel. I have 3.11.0-999 installed on my ubuntu 12.04 and it works.

---

### Post by PABlanche on 2013-08-21
Upgraded to 3.10.7. It does automount the USB thumbdrive :)
However, my screen resolution is downgraded and ... I do not see the launcher anymore, which is quite inconvenient! :(

---

### Post by VMC on 2013-08-21
Anything .xsession errors that might be helpful? Also check /var/logs.

---

