---
title: "ati 9250 fglrx, finally have module installs correctly, still freezes, lotsa info"
date: 2005-07-16
forum: Hardware &amp; Laptops
---

### Post by mjkelly on 2005-07-16
I successfully installed the linux-headers, linux-restricted-modules, and the xorg-driver all for my kernel and all of them installed correctly. My /var/log/kern.log reflects:

Jul 16 15:46:29 localhost kernel: fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jul 16 15:46:29 localhost kernel: [fglrx] Maximum main memory to use for locked dma buffers: 425 MBytes.
Jul 16 15:46:29 localhost kernel: [fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0

So the kernel loads the fully installed module correctly. When i edit my xorg.conf file to use fglrx for my device instead of ati and restart the server the system hangs, and it hangs hard. I cant ALT CTRL out of it at all. And if i play a song before starting the xserver via mpg321 and then start the server, the song freezes indicating that the whole system locked up. Also, it hangs before X has a chance to write a log file, so i cant get any EE strings out of the log.

Ive been all across the web asking for help for this. I was even on IRC the last couple days lookin for help.
Anyone have any ideas?

---

### Post by varunus on 2005-07-16
If found a page where someone talked about how they were having crashes with the ATI drivers due to the DGA extension.  Try changing this
```

Section "Modules"
....
  Load "extmod"
....
End Section
```

to this
```

Section "Modules"
   ....
  SubSection "extmod"
    Option "omit xfree86-dga"
  EndSubSection
   ....
End Section
```

Good luck.

---

### Post by mjkelly on 2005-07-17
Didnt work.

Any other suggestions?
.
EDIT: i think i might have found out whats wrong but i dont know how to fix it. Heres my Xorg.0.log.old file from one of the many times it didnt boot correctly. I grepped for fglrx.
.
@ubuntu:/var/log$ grep fglrx X*
Xorg.0.log.old:(II) LoadModule: "fglrx"
Xorg.0.log.old:(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Xorg.0.log.old:(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
============ Xorg.0.log.old:(WW) fglrx: No matching Device section for instance (BusID PCI:1:2:1) found
Xorg.0.log.old:(II) fglrx(0): pEnt->device->identifier=0x820ec50
Xorg.0.log.old:(II) fglrx(0): === [R200PreInit] === begin, [s]
Xorg.0.log.old:(II) fglrx(0): PCI bus 1 card 2 func 0
Xorg.0.log.old:(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
Xorg.0.log.old:(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
Xorg.0.log.old:(==) fglrx(0): Default visual is TrueColor
Xorg.0.log.old:(**) fglrx(0): Option "NoAccel" "no"
Xorg.0.log.old:(**) fglrx(0): Option "NoDRI" "no"
Xorg.0.log.old:(**) fglrx(0): Option "Capabilities" "0x00000000"
Xorg.0.log.old:(**) fglrx(0): Option "GammaCorrectionI" "0x00000000"
Xorg.0.log.old:(**) fglrx(0): Option "GammaCorrectionII" "0x00000000"
Xorg.0.log.old:(**) fglrx(0): Option "OpenGLOverlay" "off"
Xorg.0.log.old:(**) fglrx(0): Option "VideoOverlay" "on"
Xorg.0.log.old:(**) fglrx(0): Option "DesktopSetup" "0x00000000"
Xorg.0.log.old:(**) fglrx(0): Option "MonitorLayout" "AUTO, AUTO"
Xorg.0.log.old:(**) fglrx(0): Option "HSync2" "unspecified"
Xorg.0.log.old:(**) fglrx(0): Option "VRefresh2" "unspecified"
Xorg.0.log.old:(**) fglrx(0): Option "ScreenOverlap" "0"
Xorg.0.log.old:(**) fglrx(0): Option "IgnoreEDID" "off"
Xorg.0.log.old:(**) fglrx(0): Option "UseInternalAGPGART" "yes"
Xorg.0.log.old:(**) fglrx(0): Option "Stereo" "off"
Xorg.0.log.old:(**) fglrx(0): Option "StereoSyncEnable" "1"
Xorg.0.log.old:(**) fglrx(0): Option "UseFastTLS" "0"
Xorg.0.log.old:(**) fglrx(0): Option "BlockSignalsOnLock" "on"
Xorg.0.log.old:(**) fglrx(0): Option "ForceGenericCPU" "no"
Xorg.0.log.old:(**) fglrx(0): Option "CenterMode" "off"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAScale" "1"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAEnable" "no"
Xorg.0.log.old:(**) fglrx(0): Option "FSAADisableGamma" "no"
Xorg.0.log.old:(**) fglrx(0): Option "FSAACustomizeMSPos" "no"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosX0" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosY0" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosX1" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosY1" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosX2" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosY2" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosX3" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosY3" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosX4" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosY4" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosX5" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "FSAAMSPosY5" "0.000000"
Xorg.0.log.old:(**) fglrx(0): Option "NoTV" "yes"
Xorg.0.log.old:(**) fglrx(0): Option "TVStandard" "NTSC-M"
Xorg.0.log.old:(**) fglrx(0): Option "TVHSizeAdj" "0"
Xorg.0.log.old:(**) fglrx(0): Option "TVVSizeAdj" "0"
Xorg.0.log.old:(**) fglrx(0): Option "TVHPosAdj" "0"
Xorg.0.log.old:(**) fglrx(0): Option "TVVPosAdj" "0"
Xorg.0.log.old:(**) fglrx(0): Option "TVHStartAdj" "0"
Xorg.0.log.old:(**) fglrx(0): Option "TVColorAdj" "0"
Xorg.0.log.old:(**) fglrx(0): Option "PseudoColorVisuals" "off"
Xorg.0.log.old:(**) fglrx(0): Qbs disabled
Xorg.0.log.old:(==) fglrx(0): RGB weight 888
Xorg.0.log.old:(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
Xorg.0.log.old:(**) fglrx(0): Gamma Correction for I is 0x00000000
Xorg.0.log.old:(**) fglrx(0): Gamma Correction for II is 0x00000000
Xorg.0.log.old:(==) fglrx(0): Buffer Tiling is ON
Xorg.0.log.old:(II) fglrx(0): initializing int10
Xorg.0.log.old:(II) fglrx(0): Primary V_BIOS segment is: 0xc000
Xorg.0.log.old:(**) fglrx(0): Option "mtrr" "off"
Xorg.0.log.old:(--) fglrx(0): Chipset: "RADEON 9250 (RV280 5960)" (Chipset = 0x5960)
Xorg.0.log.old:(--) fglrx(0): (PciSubVendor = 0x148c, PciSubDevice = 0x2095)
Xorg.0.log.old:(--) fglrx(0): board vendor info: third party grafics adapter - NOT original ATI
Xorg.0.log.old:(--) fglrx(0): Linear framebuffer (phys) at 0xd8000000
Xorg.0.log.old:(--) fglrx(0): MMIO registers at 0xff8f0000
Xorg.0.log.old:(--) fglrx(0): ROM-BIOS at 0xff8c0000
Xorg.0.log.old:(--) fglrx(0): ChipExtRevID = 0x01
Xorg.0.log.old:(--) fglrx(0): ChipIntRevID = 0x00
Xorg.0.log.old:(--) fglrx(0): VideoRAM: 131072 kByte (64-bit DDR SDRAM)
Xorg.0.log.old:(WW) fglrx(0): board is an unknown third party board, chipset is supported
Xorg.0.log.old:(II) fglrx(0): I2C bus "DDC" initialized.
Xorg.0.log.old:(II) fglrx(0): Connector Layout from BIOS --------
Xorg.0.log.old:(II) fglrx(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
Xorg.0.log.old:(II) fglrx(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
Xorg.0.log.old:(**) fglrx(0): MonitorLayout Option:
Xorg.0.log.old:(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
Xorg.0.log.old:(II) fglrx(0): I2C device "DDC:ddc2" removed.
Xorg.0.log.old:(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
Xorg.0.log.old:(II) fglrx(0): I2C device "DDC:ddc2" removed.
Xorg.0.log.old:(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
Xorg.0.log.old:(II) fglrx(0): I2C device "DDC:ddc2" removed.
Xorg.0.log.old:(II) fglrx(0): DDC detected on DDCType 2 with Monitor Type 0
Xorg.0.log.old:(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
Xorg.0.log.old:(II) fglrx(0): I2C device "DDC:ddc2" removed.
Xorg.0.log.old:(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
Xorg.0.log.old:(II) fglrx(0): I2C device "DDC:ddc2" removed.

Its pointing to some device at 1:2:1. Heres my lspci

@ubuntu:/var/log$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 82)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
0000:01:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
0000:01:02.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:02.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)
0000:01:08.0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (LOM) Ethernet Controller (rev 82)

lspci also finds something at 1:2:1, but i have no idea what it is. My correct card is at 1:2:0 and xorg.conf points at it too. What is that? Would that cause xorg to hang?

---

