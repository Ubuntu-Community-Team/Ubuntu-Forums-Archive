---
title: "Like to be able to wake computer using keyboard or mouse"
date: 2015-11-30
forum: Hardware
---

### Post by Mopar1973Man on 2015-11-30
I've hunted around on the internet and I'm not finding a good answer to my problem. I would like to suspend my computer and then tap the keyboard or mouse to wake up instead of the power button. As you'll see below all my device are going into a S4 suspend which is half my problem I need to keep my keyboard and mouse at a S3 suspend level. Can anyone help me through this...???

```
michael@michael:~$ cat /proc/acpi/wakeup
Device    S-state      Status   Sysfs node
SBAZ      S4    *disabled  pci:0000:00:14.2
ECIR      S4    *disabled
PS2K      S4    *disabled
PS2M      S4    *disabled
UAR1      S4    *disabled
OHC1      S4    *enabled   pci:0000:00:12.0
EHC1      S4    *enabled   pci:0000:00:12.2
OHC2      S4    *enabled   pci:0000:00:13.0
EHC2      S4    *enabled   pci:0000:00:13.2
OHC3      S4    *disabled
EHC3      S4    *disabled
OHC4      S4    *disabled
XHC0      S4    *enabled   pci:0000:00:10.0
XHC1      S4    *enabled   pci:0000:00:10.1
PE21      S4    *disabled
PE22      S4    *disabled  pci:0000:00:15.2
RLAN      S4    *enabled   pci:0000:03:00.0
PE23      S4    *disabled
PCE2      S4    *disabled
PCE3      S4    *disabled
PCE4      S4    *disabled
PCE5      S4    *disabled
PCE6      S4    *disabled
PCE7      S4    *disabled
PE20      S4    *disabled  pci:0000:00:15.0
P0PC      S4    *disabled  pci:0000:00:14.4

```

```
michael@michael:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) I/O Memory Management Unit
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8570D]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:10.1 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 09)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 16)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] FCH PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Hudson PCI to PCI bridge (PCIE port 2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 10h-1fh) Processor Function 5
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
michael@michael:~$ 

```

---

### Post by weatherman2 on 2015-11-30
Did you look for BIOS/firmware options?

---

### Post by Mopar1973Man on 2015-11-30
The only option is for S4 suspend and its set for disable now.

---

### Post by Mopar1973Man on 2015-12-01
Very puzzled of what going on here. No right next to me is a another computer with nearly the incidental motherboards. That one will resume with tap of the keyboard but this machine will not.

My computer
```
description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=90971210-C3DE-FC2C-C092-40167E670847
  *-core
       description: Motherboard
       product: A78M-A
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: 140323639003289
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1204
          date: 12/05/2014
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 8GiB

```

MoparMom's Computer which resuming does work. I've even copied all her BIOS settings and still no love.

```
Description: Desktop Computer
    product: System Product Name (SKU)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU uuid=AD2649DD-792B-7FE8-A9AB-10C37B68B13E
  *-core
       description: Motherboard
       product: A88XM-E
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: 140424896007218
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0401
          date: 04/01/2014
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
```

---

### Post by kurt18947 on 2015-12-01
I had your problem with a recent vintage Asrock system. I used post #5 in this thread for the fix:

[http://ubuntuforums.org/showthread.php?t=1968487](http://ubuntuforums.org/showthread.php?t=1968487)

This did not work on an older Gigabyte system so there is no guarantee.

---

