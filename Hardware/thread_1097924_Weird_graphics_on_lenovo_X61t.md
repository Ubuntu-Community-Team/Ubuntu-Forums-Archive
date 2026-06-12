---
title: "Weird graphics on lenovo X61t"
date: 2009-03-16
forum: Hardware
---

### Post by kjgillis on 2009-03-16
I just installed kubuntu 8.10 using wubi. I tried running a few opengl programs including neverball. The graphics are scrambled with parts disappearing randomly. Also whenever a menu opens I see a scrambled square will the menu will appear a second before it shows up. I checked the kde hardware tool and it said I was using an intel driver. I'm not sure what the problem is and would appreciate any help. Thanks!

---

### Post by kingtaurus on 2009-03-16
Hmmm ... 
(1) Are you running with desktop effects enabled?
(2) Which version of intel driver are you using? ```
apt-cache show xserver-xorg-video-intel
```
(3) Can you post ```
/etc/X11/xorg.conf
```
(4) Can you post ```
lspci -v
```

---

### Post by kjgillis on 2009-03-16
1. Desktop effects are enabled

2.
```

kjgillis@ubuntu:~$ apt-cache show xserver-xorg-video-intel
Package: xserver-xorg-video-intel                         
Priority: optional                                        
Section: x11                                              
Installed-Size: 1024                                      
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>    
Architecture: amd64                                                       
Version: 2:2.4.1-1ubuntu10.3                                              
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-i810, xserver-xorg-video-i810 (<< 2:1.9.91-1), xserver-xorg-video-i810-modesetting, xserver-xorg-video-intel-modesetting                                                              
Provides: xserver-xorg-video-4                                                  
Depends: libc6 (>= 2.4), libdrm2 (>= 2.3.0), libpciaccess0 (>= 0.8.0+git20071002), xserver-xorg-core (>= 2:1.5.1-1ubuntu3)                                      
Conflicts: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810 (<< 2:1.9.91-1), xserver-xorg-video-i810-modesetting, xserver-xorg-video-intel-modesetting                                                                          
Filename: pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.1-1ubuntu10.3_amd64.deb                                                             
Size: 438326                                                                    
MD5sum: 54fcc49d7d3b8fba4cdb49e432321429                                        
SHA1: 47d3dc63724b4168527b55f920e31e955721cb83                                  
SHA256: 75af9d0511c41c4573890041a6ec18e90e761a9ba158a260f8598b66e23d930a        
Description: X.Org X server -- Intel i8xx, i9xx display driver                  
 This package provides the driver for the Intel i8xx and i9xx family            
 of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945          
 and i965 series chips.                                                         
 .                                                                              
 This package also provides an XvMC (XVideo Motion Compensation) driver         
 for i810 and i815 chipsets.                                                    
 .                                                                              
 More information about X.Org can be found at:                                  
 <URL:http://www.X.org>                                                         
 <URL:http://xorg.freedesktop.org>                                              
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>                       
 .                                                                              
 This package is built from the X.org xf86-video-intel driver module.           
Bugs: mailto:ubuntu-users@lists.ubuntu.com                                      
Origin: Ubuntu                                                                  
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop, mobile-mid, mobile-mobile                                                             

Package: xserver-xorg-video-intel
Priority: optional               
Section: x11                     
Installed-Size: 1024             
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>    
Architecture: amd64                                                       
Version: 2:2.4.1-1ubuntu10                                                
Replaces: xserver-xorg (<< 6.8.2-35), xserver-xorg-driver-i810, xserver-xorg-video-i810 (<< 2:1.9.91-1), xserver-xorg-video-i810-modesetting, xserver-xorg-video-intel-modesetting                                                              
Provides: xserver-xorg-video-4                                                  
Depends: libc6 (>= 2.4), libdrm2 (>= 2.3.0), libpciaccess0 (>= 0.8.0+git20071002), xserver-xorg-core (>= 2:1.5.1-1ubuntu3)                                      
Conflicts: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810 (<< 2:1.9.91-1), xserver-xorg-video-i810-modesetting, xserver-xorg-video-intel-modesetting                                                                          
Filename: pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.4.1-1ubuntu10_amd64.deb                                                               
Size: 437876                                                                    
MD5sum: 840964538945b8cc46e14763dab0170f                                        
SHA1: df48ef2beeddc9b800556ee1ccc6f7d3bd1ebe91                                  
SHA256: 1ee35e21fe3651c91591f5df9d26fecdd758b3fa73d18aa7b13e3e6fc0605e8c        
Description: X.Org X server -- Intel i8xx, i9xx display driver                  
 This package provides the driver for the Intel i8xx and i9xx family            
 of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945          
 and i965 series chips.                                                         
 .                                                                              
 This package also provides an XvMC (XVideo Motion Compensation) driver         
 for i810 and i815 chipsets.                                                    
 .                                                                              
 More information about X.Org can be found at:                                  
 <URL:http://www.X.org>                                                         
 <URL:http://xorg.freedesktop.org>                                              
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg>                       
 .                                                                              
 This package is built from the X.org xf86-video-intel driver module.           
Bugs: mailto:ubuntu-users@lists.ubuntu.com                                      
Origin: Ubuntu                                                                  
Task: ubuntu-desktop, kubuntu-desktop, edubuntu-desktop, xubuntu-desktop, mobile-mid, mobile-mobile    

```

3.
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

4.
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)                                                                  
        Subsystem: Lenovo Device 20b3                                           
        Flags: bus master, fast devsel, latency 0                               
        Capabilities: <access denied>                                           
        Kernel driver in use: agpgart-intel                                     
        Kernel modules: intel-agp                                               

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)                                                 
        Subsystem: Lenovo Device 20b5                                           
        Flags: bus master, fast devsel, latency 0, IRQ 16                       
        Memory at f8100000 (64-bit, non-prefetchable) [size=1M]                 
        Memory at e0000000 (64-bit, prefetchable) [size=256M]                   
        I/O ports at 1800 [size=8]                                              
        Capabilities: <access denied>                                           
        Kernel modules: intelfb                                                 

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)                                                        
        Subsystem: Lenovo Device 20b5                                           
        Flags: bus master, fast devsel, latency 0                               
        Memory at f8200000 (64-bit, non-prefetchable) [size=1M]                 
        Capabilities: <access denied>                                           

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)                                                                      
        Subsystem: Lenovo Device 20de                                           
        Flags: bus master, fast devsel, latency 0, IRQ 2300                     
        Memory at fe000000 (32-bit, non-prefetchable) [size=128K]               
        Memory at fe025000 (32-bit, non-prefetchable) [size=4K]                 
        I/O ports at 1840 [size=32]                                             
        Capabilities: <access denied>                                           
        Kernel driver in use: e1000e                                            
        Kernel modules: e1000e                                                  

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)                                                                  
        Subsystem: Lenovo Device 20aa                                           
        Flags: bus master, medium devsel, latency 0, IRQ 20                     
        I/O ports at 1860 [size=32]                                             
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)                                                                  
        Subsystem: Lenovo Device 20aa                                           
        Flags: bus master, medium devsel, latency 0, IRQ 21                     
        I/O ports at 1880 [size=32]                                             
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)                                                    
        Subsystem: Lenovo Device 20ab                                           
        Flags: bus master, medium devsel, latency 0, IRQ 22                     
        Memory at fe226c00 (32-bit, non-prefetchable) [size=1K]                 
        Capabilities: <access denied>                                           
        Kernel driver in use: ehci_hcd                                          
        Kernel modules: ehci-hcd                                                

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)                                                                       
        Subsystem: Lenovo Device 20ac                                           
        Flags: bus master, fast devsel, latency 0, IRQ 17                       
        Memory at fe020000 (64-bit, non-prefetchable) [size=16K]                
        Capabilities: <access denied>                                           
        Kernel driver in use: HDA Intel                                         
        Kernel modules: snd-hda-intel                                           

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)                                                                          
        Flags: bus master, fast devsel, latency 0                               
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0            
        I/O behind bridge: 00002000-00002fff                                    
        Memory behind bridge: fc000000-fdffffff                                 
        Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff    
        Capabilities: <access denied>                                           
        Kernel driver in use: pcieport-driver                                   
        Kernel modules: shpchp                                                  

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)                                                                          
        Flags: bus master, fast devsel, latency 0                               
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0            
        I/O behind bridge: 00003000-00003fff                                    
        Memory behind bridge: dc100000-dfcfffff                                 
        Prefetchable memory behind bridge: 00000000dfe00000-00000000dfefffff    
        Capabilities: <access denied>                                           
        Kernel driver in use: pcieport-driver                                   
        Kernel modules: shpchp                                                  

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)                                                                  
        Subsystem: Lenovo Device 20aa                                           
        Flags: bus master, medium devsel, latency 0, IRQ 16                     
        I/O ports at 18a0 [size=32]                                             
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)                                                                  
        Subsystem: Lenovo Device 20aa                                           
        Flags: bus master, medium devsel, latency 0, IRQ 17                     
        I/O ports at 18c0 [size=32]                                             
        Kernel driver in use: uhci_hcd                                          
        Kernel modules: uhci-hcd                                                

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)                                                    
        Subsystem: Lenovo Device 20ab                                           
        Flags: bus master, medium devsel, latency 0, IRQ 19                     
        Memory at fe227000 (32-bit, non-prefetchable) [size=1K]                 
        Capabilities: <access denied>                                           
        Kernel driver in use: ehci_hcd                                          
        Kernel modules: ehci-hcd                                                

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)                                                                             
        Flags: bus master, fast devsel, latency 0                               
        Bus: primary=00, secondary=05, subordinate=08, sec-latency=32           
        I/O behind bridge: 00004000-00007fff                                    
        Memory behind bridge: f8300000-fbffffff                                 
        Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff    
        Capabilities: <access denied>                                           

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)                                                                      
        Subsystem: Lenovo Device 20b6                                           
        Flags: bus master, medium devsel, latency 0                             
        Capabilities: <access denied>                                           
        Kernel modules: iTCO_wdt                                                

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])                                   
        Subsystem: Lenovo Device 20a6                                           
        Flags: bus master, medium devsel, latency 0, IRQ 16                     
        I/O ports at 01f0 [size=8]                                              
        I/O ports at 03f4 [size=1]                                              
        I/O ports at 0170 [size=8]                                              
        I/O ports at 0374 [size=1]                                              
        I/O ports at 18e0 [size=16]                                             
        Kernel driver in use: ata_piix                                          
        Kernel modules: ata_generic, ata_piix, pata_acpi                        

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)                                              
        Subsystem: Lenovo Device 20a7                                           
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2301            
        I/O ports at 1c30 [size=8]                                              
        I/O ports at 1c24 [size=4]                                              
        I/O ports at 1c28 [size=8]                                              
        I/O ports at 1c20 [size=4]                                              
        I/O ports at 1c00 [size=32]                                             
        Memory at fe226000 (32-bit, non-prefetchable) [size=2K]                 
        Capabilities: <access denied>                                           
        Kernel driver in use: ahci                                              
        Kernel modules: ahci                                                    

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Lenovo Device 20a9                                          
        Flags: medium devsel, IRQ 11                                           
        Memory at fe227400 (32-bit, non-prefetchable) [size=256]               
        I/O ports at 1c40 [size=32]                                            
        Kernel modules: i2c-i801                                               

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)                                                          
        Subsystem: Intel Corporation Device 1010                                
        Flags: bus master, fast devsel, latency 0, IRQ 2299                     
        Memory at dfcff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945

05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
        Subsystem: Lenovo Device 20c6
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at f8300000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=07, sec-latency=176
        Memory window 0: f4000000-f7fff000 (prefetchable)
        Memory window 1: 80000000-83fff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001
        Kernel driver in use: yenta_cardbus
        Kernel modules: yenta_socket

05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)(prog-if 10)
        Subsystem: Lenovo Device 20c7
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at f8301000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ohci1394
        Kernel modules: ohci1394

05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
        Subsystem: Lenovo Device 20c8
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at f8301800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci

```

---

### Post by kingtaurus on 2009-03-16
Can you try and disable desktop effects and see if corruption still occurs?
Can you post:
```

glxinfo | grep direct

```

---

### Post by kjgillis on 2009-03-16
Turning off KDE desktop effects seemed to solve the problem. Here's the output of that command:direct rendering: Yes

---

