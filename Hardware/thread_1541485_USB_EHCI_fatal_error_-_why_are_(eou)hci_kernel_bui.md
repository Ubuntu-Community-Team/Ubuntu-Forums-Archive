---
title: "USB EHCI fatal error - why are (e/o/u)hci kernel builtin?"
date: 2010-07-29
forum: Hardware
---

### Post by kallew on 2010-07-29
Hi,

is it normal that the USB EHCI/OHCI/UHCI drivers are built into the kernel (2.6.32-24-386 or 2.6.32.24-generic)?
I would like to sort out a hardware problem and wish to load/unload those drivers one by one, but I don't see how.

What  happens is that after some time my USB devices connected to a  USB-IDE-SATA combo-pci-card with VIA chipset somehow loose their EHCI  connection and seem to fall back to USB1.1 (UHCI). The onboard USB1.1  (SiS 745 Chipset) device has been disabled via the BIOS.

Can I disable at least OHCI in the kernel or as a module without recompiling the kernel?

The problem responsible is this ehci_hcd fatal error:

```
 <excerpt from dmesg>
 ehci_hcd 0000:00:0c.2: fatal error
 ehci_hcd 0000:00:0c.2: HC died; cleaning up
 usb 1-4: USB disconnect, address 2
 usb 3-2: new full speed USB device using uhci_hcd and address 2
 usb 3-2: not running at top speed; connect to a high speed hub
 usb 3-2: configuration #1 chosen from 1 choice
 scsi6 : SCSI emulation for USB Mass Storage devices
 usb-storage: device found at 2
 usb-storage: waiting for device to settle before scanning
 usb-storage: device scan complete
 scsi 6:0:0:0: Direct-Access     WDC WD10 EARS-00Y5B1           PQ: 0 ANSI: 2 CCS
 sd 6:0:0:0: Attached scsi generic sg3 type 0
 sd 6:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
 sd 6:0:0:0: [sdc] Write Protect is off
 sd 6:0:0:0: [sdc] Mode Sense: 28 00 00 00
 sd 6:0:0:0: [sdc] Assuming drive cache: write through
 sd 6:0:0:0: [sdc] Assuming drive cache: write through
  sdc: sdc1
 sd 6:0:0:0: [sdc] Assuming drive cache: write through
 sd 6:0:0:0: [sdc] Attached SCSI disk
 kjournald starting.  Commit interval 5 seconds
 EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
 EXT3 FS on sdc1, internal journal
 EXT3-fs: recovery complete.
 EXT3-fs: mounted filesystem with ordered data mode.
 kjournald starting.  Commit interval 5 seconds
 EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
 EXT3 FS on sdc1, internal journal
 EXT3-fs: mounted filesystem with ordered data mode.
 usb 3-2: USB disconnect, address 2

``````

kallew@rom:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 745 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0a.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
00:0c.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0c.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0c.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
00:0c.3 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

``````

kallew@rom:~$ cat /boot/config-2.6.32-24-386 | grep -i hci
CONFIG_BT_HCIBTUSB=m
CONFIG_BT_HCIBTSDIO=m
CONFIG_BT_HCIUART=m
CONFIG_BT_HCIUART_H4=y
CONFIG_BT_HCIUART_BCSP=y
CONFIG_BT_HCIUART_LL=y
CONFIG_BT_HCIBCM203X=m
CONFIG_BT_HCIBPA10X=m
CONFIG_BT_HCIBFUSB=m
CONFIG_BT_HCIDTL1=m
CONFIG_BT_HCIBT3C=m
CONFIG_BT_HCIBLUECARD=m
CONFIG_BT_HCIBTUART=m
CONFIG_BT_HCIVHCI=m
CONFIG_SATA_AHCI=m
CONFIG_FIREWIRE_OHCI=m
CONFIG_FIREWIRE_OHCI_DEBUG=y
CONFIG_IEEE1394_OHCI1394=m
CONFIG_USB_ARCH_HAS_OHCI=y
CONFIG_USB_ARCH_HAS_EHCI=y
CONFIG_USB_XHCI_HCD=m
# CONFIG_USB_XHCI_HCD_DEBUGGING is not set
CONFIG_USB_EHCI_HCD=y
CONFIG_USB_EHCI_ROOT_HUB_TT=y
CONFIG_USB_EHCI_TT_NEWSCHED=y
CONFIG_USB_OHCI_HCD=y
# CONFIG_USB_OHCI_BIG_ENDIAN_DESC is not set
# CONFIG_USB_OHCI_BIG_ENDIAN_MMIO is not set
CONFIG_USB_OHCI_LITTLE_ENDIAN=y
CONFIG_USB_UHCI_HCD=y
CONFIG_USB_WHCI_HCD=m
CONFIG_UWB_WHCI=m
CONFIG_MMC_SDHCI=m
CONFIG_MMC_SDHCI_PCI=m
CONFIG_MMC_SDHCI_PLTFM=m
CONFIG_USB_IP_VHCI_HCD=m
# CONFIG_PROVIDE_OHCI1394_DMA_INIT is not set
# CONFIG_FIREWIRE_OHCI_REMOTE_DMA is not set

```

---

