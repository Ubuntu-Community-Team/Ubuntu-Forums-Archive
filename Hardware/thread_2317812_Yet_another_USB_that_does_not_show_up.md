---
title: "Yet another USB that does not show up"
date: 2016-03-20
forum: Hardware
---

### Post by andyhelloween on 2016-03-20
Hello everyone,

I'm running an Ubuntu Server 14.04 install - 3.13.0-83-generic

I have an Apacer memory card reader that comes with a handy USB3 port. Plugged a Kingston stick in there, all good until fdisk... it does not show up. The USB is encrypted with cryptsetup. I can access it perfectly fine in other Ubuntu installs. Any help out there?

dmesg:

```
[95022.623213] usb 3-2: new high-speed USB device number 3 using xhci_hcd
[95022.643110] usb 3-2: New USB device found, idVendor=0951, idProduct=1666
[95022.643115] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[95022.643118] usb 3-2: Product: DataTraveler 3.0
[95022.643120] usb 3-2: Manufacturer: Kingston
[95022.643122] usb 3-2: SerialNumber: 08606E6D41B3BE3057019249
[95022.643869] usb-storage 3-2:1.0: USB Mass Storage device detected
[95022.643971] scsi17 : usb-storage 3-2:1.0
```

dmesg in another Ubuntu installation

```
[ 3297.923094] usb 1-1.2: new high-speed USB device number 5 using ehci-pci
[ 3298.025516] usb 1-1.2: New USB device found, idVendor=0951, idProduct=1666
[ 3298.025524] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3298.025528] usb 1-1.2: Product: DataTraveler 3.0
[ 3298.025531] usb 1-1.2: Manufacturer: Kingston
[ 3298.025534] usb 1-1.2: SerialNumber: 08606E6D41B3BE3057019249
[ 3298.077361] usb-storage 1-1.2:1.0: USB Mass Storage device detected
[ 3298.077662] scsi6 : usb-storage 1-1.2:1.0
[ 3298.077732] usbcore: registered new interface driver usb-storage
[ 3299.076596] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 3.0 PMAP PQ: 0 ANSI: 6
[ 3299.077157] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 3299.077927] sd 6:0:0:0: [sdb] 61440000 512-byte logical blocks: (31.4 GB/29.2 GiB)
[ 3299.079515] sd 6:0:0:0: [sdb] Write Protect is off
[ 3299.079522] sd 6:0:0:0: [sdb] Mode Sense: 2b 80 00 08
[ 3299.081143] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 3299.342499]  sdb: sdb1
[ 3299.348055] sd 6:0:0:0: [sdb] Attached SCSI removable disk
```


lsusb

```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 1058:0820 Western Digital Technologies, Inc. My Passport Ultra (WDBMWV, WDBZFP)
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bda:0301 Realtek Semiconductor Corp. multicard reader
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 03f0:2404 Hewlett-Packard Deskjet F2280 series
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsmod | grep usb_storage
```
usb_storage            62209  1 
```

fdisk -l

```
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004f6f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   83  Linux

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0080cba1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   609374207   304686080   83  Linux
/dev/sda2       609376254   625141759     7882753    5  Extended
/dev/sda5       609376256   625141759     7882752   82  Linux swap / Solaris

Disk /dev/sdh: 2000.4 GB, 2000365289472 bytes
58 heads, 60 sectors/track, 1122690 cylinders, total 3906963456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x258842f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1            2048  3906963455  1953480704   83  Linux

Disk /dev/mapper/backup: 2000.4 GB, 2000362143744 bytes
255 heads, 63 sectors/track, 243196 cylinders, total 3906957312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/backup doesn't contain a valid partition table
```

Thanks,
A.

---

### Post by sudodus on 2016-03-20
Could be that the 'Apacer memory card reader that comes with a handy USB3 port' cannot cooperate with the computer or with this Kingston pendrive.

Have you tried if this Kingston pendrive can be seen and used in another USB 2 or USB 3 port on the computer?

Have you tried if another pendrive can be seen and used with your Apacer memory card reader?

In all these cases, what is the output of the following commands?

```
sudo fdisk -lu

sudo lsblk -fm
```

---

### Post by oldfred on 2016-03-20
What motherboard? 
Some like Gigabyte need iommu settings changed in UEFI and boot parameter.
But if other USB ports working that should not be the issue.

---

### Post by andyhelloween on 2016-09-25
Apologies for the long long delay in my response.

It turns out there was some sort of failure in the USB stick. It worked in another computer but throwing error after error upon accessing files in it.

Thank you very much for your time.

---

