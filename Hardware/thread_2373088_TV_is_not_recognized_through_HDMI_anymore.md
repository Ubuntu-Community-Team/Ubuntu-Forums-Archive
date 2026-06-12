---
title: "TV is not recognized through HDMI anymore"
date: 2017-10-02
forum: Hardware
---

### Post by godspeedyou on 2017-10-02
I have had a dual monitor (one tv, one monitor) setup for a few month  on Ubuntu 16.04.3 LTS. And I've had this setup before for a few years  on xubuntu 14 and older.
  Whenever I've watched some MP4 videos with Totem on Ubuntu 16  sometimes the screens started reconfiguring and sometimes one of the  screens wasn't recognized anymore. This all reconfigured itself usually.  However, this time the tv screen (LG32LC52) isn't detected anymore even  if I restart the pc. 
  The tv screen is connected to HDMI-0. Unplugging and plugging the  hdmi cable has no effect. I checked the hdmi cable and the tv screen on  another pc device. They are working.
  Additionally all videos played with Totem and Youtube now play in double speed, although normal speed is activated.
  I rebooted the pc and switched to Kubuntu 14 and Win 7. No HDMI as well. I replaced the graphic card with another one and still no HDMI. Might this be a motherboard issue?
  ```
xrandr --current
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080     60.00*+
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.91  
   1024x768      60.00  
   800x600       60.32    56.25  
   640x480       60.00  
  
```
My graphics card:

  ```
lspci | grep VGA
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV730 PRO [Radeon HD 4650]

```  I used the hdmi port of my monitor - this works! So the monitor works  via hdmi port, but only the tv is not, although the tv works on my  notebook
  ```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.91  
   1280x720      60.00    50.00    59.94  
   1024x768      60.00  
   800x600       60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       60.00    59.94  

```  Funny how this states the VGA port is connected.
  I freshly installed Ubuntu 16, but the problems persist. I switched to the aforementioned other graphics card, which is the following:
  ```
lspci | grep VGA
05:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400 GS] (rev a1)

```  I turned on the nvidia-304 drivers (304.137) in the Applications  & Updates -> Additional drivers section. I would have the option  to switch to nvidia-340 (340.104) or Nouveau. Those do not recognize the  tv at all though.
  It recognizes the tv. But only as a vga device with a resolution of 800x600, although it is still connected via hdmi.
  ```
xrandr --current
Screen 0: minimum 8 x 8, current 2720 x 1080, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 1920x1080+800+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1600x1200     60.00  
   1440x900      59.89  
   1280x1024     60.02  
   1280x960      60.00  
   1280x800      59.81  
   1024x768      60.00  
   800x600       60.32    56.25  
   640x480       59.94  
VGA-0 connected 800x600+0+480 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600       60.32*+

```  I have the feeling the Totem crash caused an EDID corruption and only Windows still can recognize the tv(?). If so I'd need details on how to fix this.
  I have no clue as to how to debug this behavior any further.

I still have my old 16.04 distribution aside. When I boot it, I can see the following message several times in the kern.log:
  ```

kernel: [  519.320215] nouveau 0000:05:00.0: DRM: DDC responded, but no EDID for VGA-1

```
  I have no clue as to how to debug this behavior any further.

---

### Post by efflandt on 2017-10-03
I am not familiar with many ATI/AMD cards, but yours is old enough that there would not be anything other than the default radeon driver for it.

The 8400 GS is very old and I am not sure which proprietary nvidia driver version would support it. The fact that you see nouveau instead of nvidia in logs means that it is likely using the default nouveau driver. Although, VGA-1 error is puzzling when xrandr does not show any VGA-1 output for the Nvidia card.

I cannot explain why connecting a display with HDMI (or even DVI to HDMI) would show up as VGA, because HDMI and DVI are both digital. The only time that might happen is if connected DVI to VGA which would use the analog video pins of DVI-I.

I am using a 32" 1080p LG HDTV as single monitor, but not sure of the model that I have had for possibly 5 years of more. It has 2 ms response time and can simulate 120 Hz refresh using interpolation. I have mostly had it connected DVI to HDMI since I was using my HDMI cables for other things and I think my current graphics card might be mini-HDMI.

The following in a terminal would show which drivers (modules) are being used for graphics:```
sudo lspci -v
```

---

### Post by godspeedyou on 2017-10-04
Thanks for your reply.
```

 sudo lspci -v
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RX790 Host Bridge
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RX790 Host Bridge
    Flags: bus master, 66MHz, medium devsel, latency 0
    Memory at <ignored> (64-bit, non-prefetchable)
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [9c] HyperTransport: #1a

00:02.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RD790 PCI to PCI bridge (external gfx0 port A) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fa000000-fe9fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RX780/RD790 PCI to PCI bridge (external gfx0 port A)
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:09.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port E) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 25
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: f9f00000-f9ffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port E)
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0a.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port F) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f9e00000-f9efffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD790 PCI to PCI bridge (PCI express gpp port F)
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40) (prog-if 01 [AHCI 1.0])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 35
    I/O ports at a000 [size=8]
    I/O ports at 9000 [size=4]
    I/O ports at 8000 [size=8]
    I/O ports at 7000 [size=4]
    I/O ports at 6000 [size=16]
    Memory at f9cfa000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] MSI: Enable+ Count=1/4 Maskable- 64bit+
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f9cf3000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f9cfa400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci

00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f9cf8000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f9cfa800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 41)
    Flags: 66MHz, medium devsel
    Kernel modules: i2c_piix4, sp5100_tco

00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40) (prog-if 8a [Master SecP PriP])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4
    I/O ports at 0170 [size=8]
    I/O ports at 0374
    I/O ports at ff00 [size=16]
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp, pata_acpi

00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f9cf4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: f9d00000-f9dfffff

00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f9cf9000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Prefetchable memory behind bridge: 00000000cff00000-00000000cfffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:16.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f9cfb000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci

00:16.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f9cfac00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci-pci

00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards
    Flags: bus master, fast devsel, latency 0, IRQ 36
    I/O ports at b800 [size=256]
    Memory at cffff000 (64-bit, prefetchable) [size=4K]
    Memory at cfff8000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169

02:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Motherboard
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at f9dff800 (32-bit, non-prefetchable) [size=2K]
    I/O ports at cc00 [size=128]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci

03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30 [XHCI])
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at f9efe000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [50] Power Management version 3
    Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
    Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
    Capabilities: [a0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
    Capabilities: [150] Latency Tolerance Reporting
    Kernel driver in use: xhci_hcd

04:00.0 SATA controller: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. JMB361 AHCI/IDE
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f9ffe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [68] Power Management version 2
    Capabilities: [50] Express Legacy Endpoint, MSI 01
    Kernel driver in use: ahci
    Kernel modules: ahci

04:00.1 IDE interface: JMicron Technology Corp. JMB361 AHCI/IDE (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. JMB361 AHCI/IDE
    Flags: bus master, fast devsel, latency 0, IRQ 18
    I/O ports at dc00 [size=8]
    I/O ports at d880 [size=4]
    I/O ports at d800 [size=8]
    I/O ports at d480 [size=4]
    I/O ports at d400 [size=16]
    Capabilities: [68] Power Management version 2
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron, pata_acpi

05:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400 GS] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: CardExpert Technology G86 [GeForce 8400 GS]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_304

```

---

### Post by efflandt on 2017-10-05
Ok that looks like it is using the nvidia module (driver).

Sorry I cannot help you. I did have an issue with 16.04 initially only with one computer, blank display throughout BIOS splash and grub menu until an OS did graphics (Ubuntu gui login or Win7 depending upon what was previously set as default). Not sure what caused that, because (something in graphics left in an unusual state) because it would persist for one more boot after the drive was removed. And that drive works fine with 16.10 (which has reached end of support) or 16.04 on any other computer. I had no problems after reaching Ubuntu 16.04, only the blank during boot issue with only 1 PC. I am expecting to receive an SSD Friday and need to determine whether 16.04.3 LTS will work for me now or whether I need to move onto shorter term 17.04.

---

### Post by godspeedyou on 2017-10-05
Regarding your first post, do you think a newer graphic card could do the trick?

---

