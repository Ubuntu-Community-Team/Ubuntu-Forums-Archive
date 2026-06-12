---
title: "External hard drive won't mount after 12.04 install"
date: 2012-11-16
forum: Hardware
---

### Post by dr_dred5 on 2012-11-16
I installed Ubuntu 12.04 yesterday. It was a clean install, I deleted the partition that used to contain 10.04 and started from scratch.

I have three different distros installed on my system and all of them are working flawlessly.

The thing that confuses me the most, is that my external drive was disconnected during the install. I booted into an older version (9.04) and it was working fine. Buy ehen I booted into 12.04 it had vanished and now won't work in any of my distros.

Gparted does not detect it, but storage device manager does, without any partitions and it won't let me mount it.

The HD is an Iomega 1Tb. It is listed as sdc. I've done a fair bit of research on this. Here are some output files.

From dmesg after connecting.
```
sudo dmesg
[  339.836027] usb 1-6: new high-speed USB device number 3 using ehci_hcd
[  340.058004] Initializing USB Mass Storage driver...
[  340.058192] scsi2 : usb-storage 1-6:1.0
[  340.058357] usbcore: registered new interface driver usb-storage
[  340.058360] USB Mass Storage support registered.
[  340.064613] usbcore: registered new interface driver uas
[  341.056769] scsi 2:0:0:0: Direct-Access     ST310005 28AS                  PQ: 0 ANSI: 2 CCS
[  341.063579] sd 2:0:0:0: Attached scsi generic sg4 type 0
[  341.064437] sd 2:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[  341.065603] sd 2:0:0:0: [sdc] 72057594037927936 512-byte logical blocks: (0 B/0 B)
[  341.066384] sd 2:0:0:0: [sdc] Write Protect is off
[  341.066391] sd 2:0:0:0: [sdc] Mode Sense: 28 00 00 00
[  341.067128] sd 2:0:0:0: [sdc] No Caching mode page present
[  341.067136] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  341.067989] sd 2:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[  341.071759] sd 2:0:0:0: [sdc] No Caching mode page present
[  341.071768] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  341.072197]  sdc: unknown partition table
[  341.074581] sd 2:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[  341.076762] sd 2:0:0:0: [sdc] No Caching mode page present
[  341.076771] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  341.076776] sd 2:0:0:0: [sdc] Attached SCSI disk
```

lsusb

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4de4 Primax Electronics, Ltd 
Bus 001 Device 003: ID 059b:0475 Iomega Corp.
```

fdisk -l

```
sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x069ae558

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    58593812    29296875   83  Linux
/dev/sda2       485307585   488392064     1542240   82  Linux swap / Solaris
/dev/sda3       267932070   485307584   108687757+  83  Linux
/dev/sda4        58595326   267931647   104668161    5  Extended
/dev/sda5       246999375   267916004    10458315   83  Linux
/dev/sda6        58605183   246999374    94197096   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bca7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156296384    78148161   83  Linux
```

lsusb -v
```
Bus 001 Device 003: ID 059b:0475 Iomega Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x059b Iomega Corp.
  idProduct          0x0475 
  bcdDevice            0.00
  iManufacturer          10 Iomega
  iProduct               11 USB to ATA/ATAPI bridge
  iSerial                 3 325000000046
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 USB Mass Storage
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              6 MSC Bulk-Only Transfer
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered
```

Parted

```
(parted) print list,all                                                   
Model: ATA WDC WD2500JB-00G (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  30.0GB  30.0GB  primary   ext4            boot
 4      30.0GB  137GB   107GB   extended
 6      30.0GB  126GB   96.5GB  logical   ext3
 5      126GB   137GB   10.7GB  logical   ext4
 3      137GB   248GB   111GB   primary   ext3
 2      248GB   250GB   1579MB  primary   linux-swap(v1)


Model: ATA WDC WD800BB-00DA (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
```

lvscan

```
sudo lvscan -a
  No volume groups found

```

testdisk detected the drive but seemed unable to do anything with it.

```
Select a media (use Arrow keys, then press Enter):
 Disk /dev/sda - 250 GB / 232 GiB - WDC WD2500JB-00GVC0
 Disk /dev/sdb - 80 GB / 74 GiB - WDC WD800BB-00DAA3
>[COLOR="Red"]Disk /dev/sdc - 539 GB / 502 GiB - ST310005 28AS[/COLOR]
 Disk /dev/sdd - 2055 MB / 1960 MiB
```

After analising twice all I get is Read Errors during the scans and the following output.

```
Disk /dev/sdc - 539 GB / 502 GiB - CHS 65535 255 63

     Partition                  Start        End    Size in sectors


No partition found or selected for recovery
```

I'm not sure where to go from here. Any help would be greatly appreciated.

---

