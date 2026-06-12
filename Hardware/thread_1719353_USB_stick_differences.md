---
title: "USB stick differences"
date: 2011-04-01
forum: Hardware
---

### Post by ceperman on 2011-04-01
I recently created a live Clonezilla USB stick which booted successfully on all my computers except one (an EPIA VIA system) - on this system the USB stick was not even detected. I have a number of USB sticks, all of which are formatted as FAT32 and so you'd think they'd look the same, but in act they all appear different (in the Device Manager). 
This is a screen shot:
[IMG]https://picasaweb.google.com/ceperman/Private?authkey=Gv1sRgCKf4kLmp2Puo-wE#[/IMG]

In case the screen shot doesn't show, the info looks like this:

Peripheral Devices
USB, Firewire and other peripherals

  251 MB Hard Disk
  USB Flash Disk

  General USB Flash Disk
  General USB Flash Disk

  Kingston DataTraveler2.0
  Kingston DataTraveler2.0

  USB DISK 2.0
  USB DISK 2.0

  Integral Courier
  Integral Courier


The odd one out is the first, and you can see it shows up as a USB HDD instead of a flash drive.

Syslog for the insertion of the devices shows this info (suitably annotated by me):

251 MB Hard Disk
Apr  1 17:56:12 home kernel: [ 1831.448057] usb 1-7.2: new high speed USB device using ehci_hcd and address 3
Apr  1 17:56:12 home kernel: [ 1831.601932] Initializing USB Mass Storage driver...
Apr  1 17:56:12 home kernel: [ 1831.602057] scsi4 : usb-storage 1-7.2:1.0
Apr  1 17:56:12 home kernel: [ 1831.602400] usbcore: registered new interface driver usb-storage
Apr  1 17:56:12 home kernel: [ 1831.602403] USB Mass Storage support registered.
Apr  1 17:56:14 home kernel: [ 1833.529730] scsi 4:0:0:0: Direct-Access     USB      Flash Disk       1100 PQ: 0 ANSI: 0 CCS
Apr  1 17:56:14 home kernel: [ 1833.530225] sd 4:0:0:0: Attached scsi generic sg2 type 0
Apr  1 17:56:14 home kernel: [ 1833.532442] sd 4:0:0:0: [sdb] 489472 512-byte logical blocks: (250 MB/239 MiB)
Apr  1 17:56:14 home kernel: [ 1833.533220] sd 4:0:0:0: [sdb] Write Protect is off
Apr  1 17:56:14 home kernel: [ 1833.533224] sd 4:0:0:0: [sdb] Mode Sense: 43 00 00 00
Apr  1 17:56:14 home kernel: [ 1833.533227] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Apr  1 17:56:14 home kernel: [ 1833.534818] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Apr  1 17:56:14 home kernel: [ 1833.534823]  sdb: sdb1
Apr  1 17:56:14 home kernel: [ 1833.537944] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Apr  1 17:56:14 home kernel: [ 1833.537948] sd 4:0:0:0: [sdb] Attached SCSI disk

General USB Flash Disk
Apr  1 17:56:59 home kernel: [ 1878.812103] usb 1-7.3: new high speed USB device using ehci_hcd and address 4
Apr  1 17:56:59 home kernel: [ 1878.921625] scsi5 : usb-storage 1-7.3:1.0
Apr  1 17:57:00 home kernel: [ 1879.922680] scsi 5:0:0:0: Direct-Access     General  USB Flash Disk   1.00 PQ: 0 ANSI: 2
Apr  1 17:57:00 home kernel: [ 1879.923177] sd 5:0:0:0: Attached scsi generic sg3 type 0
Apr  1 17:57:00 home kernel: [ 1879.923794] sd 5:0:0:0: [sdc] 3913728 512-byte logical blocks: (2.00 GB/1.86 GiB)
Apr  1 17:57:00 home kernel: [ 1879.924947] sd 5:0:0:0: [sdc] Write Protect is off
Apr  1 17:57:00 home kernel: [ 1879.924952] sd 5:0:0:0: [sdc] Mode Sense: 0b 00 00 08
Apr  1 17:57:00 home kernel: [ 1879.924955] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Apr  1 17:57:00 home kernel: [ 1879.926790] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Apr  1 17:57:00 home kernel: [ 1879.926797]  sdc: sdc1
Apr  1 17:57:01 home kernel: [ 1879.929033] sd 5:0:0:0: [sdc] Assuming drive cache: write through
Apr  1 17:57:01 home kernel: [ 1879.929037] sd 5:0:0:0: [sdc] Attached SCSI removable disk

Kingston DataTraveller2.0
Apr  1 17:57:36 home kernel: [ 1915.416061] usb 1-7.4: new full speed USB device using ehci_hcd and address 5
Apr  1 17:57:36 home kernel: [ 1915.592047] usb 1-7.4: new high speed USB device using ehci_hcd and address 6
Apr  1 17:57:36 home kernel: [ 1915.702454] scsi6 : usb-storage 1-7.4:1.0
Apr  1 17:57:37 home kernel: [ 1916.700865] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler2.0  1.00 PQ: 0 ANSI: 2
Apr  1 17:57:37 home kernel: [ 1916.701357] sd 6:0:0:0: Attached scsi generic sg4 type 0
Apr  1 17:57:37 home kernel: [ 1916.702816] sd 6:0:0:0: [sdd] 1955711 512-byte logical blocks: (1.00 GB/954 MiB)
Apr  1 17:57:37 home kernel: [ 1916.703351] sd 6:0:0:0: [sdd] Write Protect is off
Apr  1 17:57:37 home kernel: [ 1916.703355] sd 6:0:0:0: [sdd] Mode Sense: 0b 00 00 08
Apr  1 17:57:37 home kernel: [ 1916.703358] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Apr  1 17:57:37 home kernel: [ 1916.706096] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Apr  1 17:57:37 home kernel: [ 1916.706101]  sdd: sdd1
Apr  1 17:57:37 home kernel: [ 1916.733097] sd 6:0:0:0: [sdd] Assuming drive cache: write through
Apr  1 17:57:37 home kernel: [ 1916.733101] sd 6:0:0:0: [sdd] Attached SCSI removable disk

USB DISK 2.0
Apr  1 17:58:10 home kernel: [ 1949.204107] usb 1-7.1: new high speed USB device using ehci_hcd and address 7
Apr  1 17:58:10 home kernel: [ 1949.322391] scsi7 : usb-storage 1-7.1:1.0
Apr  1 17:58:11 home kernel: [ 1950.321417] scsi 7:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
Apr  1 17:58:11 home kernel: [ 1950.321912] sd 7:0:0:0: Attached scsi generic sg5 type 0
Apr  1 17:58:11 home kernel: [ 1950.762612] sd 7:0:0:0: [sde] 7831552 512-byte logical blocks: (4.00 GB/3.73 GiB)
Apr  1 17:58:11 home kernel: [ 1950.763107] sd 7:0:0:0: [sde] Write Protect is off
Apr  1 17:58:11 home kernel: [ 1950.763110] sd 7:0:0:0: [sde] Mode Sense: 23 00 00 00
Apr  1 17:58:11 home kernel: [ 1950.763113] sd 7:0:0:0: [sde] Assuming drive cache: write through
Apr  1 17:58:11 home kernel: [ 1950.765236] sd 7:0:0:0: [sde] Assuming drive cache: write through
Apr  1 17:58:11 home kernel: [ 1950.765242]  sde: sde1 sde2 sde3 sde4
Apr  1 17:58:11 home kernel: [ 1950.767111] sd 7:0:0:0: [sde] Assuming drive cache: write through
Apr  1 17:58:11 home kernel: [ 1950.767115] sd 7:0:0:0: [sde] Attached SCSI removable disk

Integral Courier
Apr  1 17:58:51 home kernel: [ 1990.780021] usb 1-4: new high speed USB device using ehci_hcd and address 8
Apr  1 17:58:51 home kernel: [ 1990.915862] scsi8 : usb-storage 1-4:1.0
Apr  1 17:58:53 home kernel: [ 1992.002726] scsi 8:0:0:0: Direct-Access     Integral Courier          PMAP PQ: 0 ANSI: 0 CCS
Apr  1 17:58:53 home kernel: [ 1992.003288] sd 8:0:0:0: Attached scsi generic sg6 type 0
Apr  1 17:58:53 home kernel: [ 1992.326629] sd 8:0:0:0: [sdf] 7834944 512-byte logical blocks: (4.01 GB/3.73 GiB)
Apr  1 17:58:53 home kernel: [ 1992.327119] sd 8:0:0:0: [sdf] Write Protect is off
Apr  1 17:58:53 home kernel: [ 1992.327122] sd 8:0:0:0: [sdf] Mode Sense: 23 00 00 00
Apr  1 17:58:53 home kernel: [ 1992.327125] sd 8:0:0:0: [sdf] Assuming drive cache: write through
Apr  1 17:58:53 home kernel: [ 1992.328994] sd 8:0:0:0: [sdf] Assuming drive cache: write through
Apr  1 17:58:53 home kernel: [ 1992.328999]  sdf: sdf1
Apr  1 17:58:53 home kernel: [ 1992.343501] sd 8:0:0:0: [sdf] Assuming drive cache: write through
Apr  1 17:58:53 home kernel: [ 1992.343505] sd 8:0:0:0: [sdf] Attached SCSI removable disk

Can anyone explain what the differences are and why, and why the VIA EPIA computer doesn't detect the 251 MB Hard Disk?

Chris Wood

---

