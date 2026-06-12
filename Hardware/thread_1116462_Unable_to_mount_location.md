---
title: "Unable to mount location"
date: 2009-04-04
forum: Hardware
---

### Post by yawnmoth on 2009-04-04
I have a 120GB SATA hard drive that I'm trying to mount via a USB <-> SATA adapter.  Whenever I try, however, I get a "Unable to mount location: Can't mount file" error.

Here's the output of "dmesg | tail -n 50":

```
[   71.107748] apm: overridden by ACPI.
[   71.431219] lp: driver loaded but no devices found
[   71.532577] ppdev: user-space parallel port driver
[   76.614790] Bluetooth: Core ver 2.13
[   76.617576] NET: Registered protocol family 31
[   76.617584] Bluetooth: HCI device and connection manager initialized
[   76.617589] Bluetooth: HCI socket layer initialized
[   76.743640] Bluetooth: L2CAP ver 2.11
[   76.743648] Bluetooth: L2CAP socket layer initialized
[   77.024305] Bluetooth: RFCOMM socket layer initialized
[   77.024696] Bluetooth: RFCOMM TTY layer initialized
[   77.024708] Bluetooth: RFCOMM ver 1.10
[   77.044878] Bluetooth: SCO (Voice Link) ver 0.6
[   77.044887] Bluetooth: SCO socket layer initialized
[   77.261562] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   77.261571] Bluetooth: BNEP filters: protocol multicast
[   77.401159] Bridge firewalling registered
[   77.402363] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   82.072735] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   83.609077] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   83.760466] NET: Registered protocol family 17
[   84.048202] [drm] Initialized drm 1.1.0 20060810
[   84.109910] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   84.683615] [drm] Setting GART location based on new memory map
[   84.685441] [drm] Loading R300 Microcode
[   84.685495] [drm] Num pipes: 2
[   84.685503] [drm] writeback test succeeded in 1 usecs
[   91.387167] hda-intel: Invalid position buffer, using LPIB read method instead.
[  176.760038] usb 1-5: new high speed USB device using ehci_hcd and address 3
[  176.922522] usb 1-5: configuration #1 chosen from 1 choice
[  177.421530] usbcore: registered new interface driver libusual
[  177.492023] Initializing USB Mass Storage driver...
[  177.495073] scsi6 : SCSI emulation for USB Mass Storage devices
[  177.496380] usbcore: registered new interface driver usb-storage
[  177.496778] USB Mass Storage support registered.
[  177.497217] usb-storage: device found at 3
[  177.497224] usb-storage: waiting for device to settle before scanning
[  182.496308] usb-storage: device scan complete
[  182.497530] scsi 6:0:0:0: Direct-Access     TOSHIBA  MK1237GSX        0G   PQ: 0 ANSI: 2 CCS
[  182.537017] sd 6:0:0:0: [sdc] 234441648 512-byte hardware sectors (120034 MB)
[  182.538432] sd 6:0:0:0: [sdc] Write Protect is off
[  182.538443] sd 6:0:0:0: [sdc] Mode Sense: 00 38 00 00
[  182.538446] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  182.544333] sd 6:0:0:0: [sdc] 234441648 512-byte hardware sectors (120034 MB)
[  182.546866] sd 6:0:0:0: [sdc] Write Protect is off
[  182.546877] sd 6:0:0:0: [sdc] Mode Sense: 00 38 00 00
[  182.546881] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  182.547608]  sdc:
[  182.912696] sd 6:0:0:0: [sdc] Attached SCSI disk
[  182.913204] sd 6:0:0:0: Attached scsi generic sg3 type 0
```

Any ideas?

---

### Post by taurus on 2009-04-04
Is it a brand new drive?  Have you created a partition and formatted it (filesystem)?

```
sudo fdisk -l
```

---

### Post by yawnmoth on 2009-04-05
I partitioned it with fdisk and tried to format it with "sudo mkfs -t ntfs /dev/sdc1" and this is what I got:

```
Cluster size has been automatically set to 4096 bytes.
Initializing device with zeroes: 100% - Done.
Creating NTFS volume structures.
Error writing to /dev/sdc1: Input/output error.
Error writing non-resident attribute value.
add_attr_sd failed: Input/output error
Couldn't create root directory: Input/outpt error
```
Any ideas?  Is the drive dead?

---

### Post by cariboo on 2009-04-05
I think you may be better off using gparted to partition and format your drive. Gparted is in the repositories. Once installed go to System-->Administration-->Partition Editor, the rest is pretty obvious from there.

Jim

---

