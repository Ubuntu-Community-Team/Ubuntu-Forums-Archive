---
title: "Ubuntu freeze when I try to use Nvidia PCI 8400"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by 2discover on 2009-04-13
My system has two video cards I can run windows XP with both but I'm having problems with Ubuntu when I try to use the new Nvidia card. Here is some information about my system. Hope someone can help me disable my Intel integrated card so when ubuntu starts up it can fully load-up reading only the nvidia card. Thanks 

Ubuntu release 9.04 (jaunty)
Kernel Linux 2.6.28-11-generic
GNOME 2.26.0
Hardware
memory 1001.6 Mib
processor: Intel ® Pentium ®  4 CPU 2.00GHz
 
lspci | grep VGA 
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) 
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1) 


lspci 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) 
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02) 
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) 
01:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01) 
01:06.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa) 
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01) 
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1) 

Sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf". 

WARNING: No Layout specified, constructing implicit layout section using screen 
         "Default Screen". 


WARNING: Unable to find CorePointer in X configuration; attempting to add new 
         CorePointer section. 


WARNING: The CorePointer device was not specified explicitly in the layout; 
         using the first mouse device. 


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new 
         CoreKeyboard section. 


WARNING: The CoreKeyboard device was not specified explicitly in the layout; 
         using the first keyboard device. 

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup' 
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by 2discover on 2009-04-13
Found what I was looking for  [http://www.fixya.com/support/t172771-dell_dimension_2350_reboot](http://www.fixya.com/support/t172771-dell_dimension_2350_reboot)

 I follow solution #1 and problem solve.Hope this helps someone else!!!

I have the exact same PC and problem with all versions of linux I have tried from Mepis, Ubuntu, etc.

Problem is the bios appears to be buggy. Linux boot will find the onboard video even if you have the bios set to use your MX4000 PCI card. Linux boot freezes with different error messages.

Easy fix is to just use the onboard video. Of course if you wanted to do that you wouldn't have bought the card right?

What I have done is first I use the onboard video to install say Ubuntu Linux. You don't even have to remove the PCI video card.

Step by step:
1. set bios to use onboard video, and connect your monitor to the onboard video port.

2. in terminal: sudo gedit /etc/modprobe.d/blacklist
add these lines to the end
blacklist agpgart
blacklist intel_agp
press control-X to save your changes
After you install you have to "blacklist" the onboard video.

3. shut down linux. besure to power down the PC because its just easier to bet into bios from a hard boot.

4. go to bios and set video to "auto" and save your change.

5. move your monitor cable to the MX4000 PCI video card

that should do it. any trouble just search ubuntu forums for blacklist agpgart or intel_agp

---

