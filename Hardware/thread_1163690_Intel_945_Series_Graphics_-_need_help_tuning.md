---
title: "Intel 945 Series Graphics - need help tuning"
date: 2009-05-18
forum: Hardware
---

### Post by k3tchup on 2009-05-18
Hello everyone, 

I am running Ubuntu 9.04 NBR on my HP mini 1030nr (netbook).   According to lspci output, it comes equipped with an Intel Corporation Mobile 945GME Express Integrated Graphics Controller.   It is using intel_agp / intelfb modules.  My issue is that video peformance is choppy.  I get crappy playback on youtube for example and firefox scrolling is annoyingly choppy.    

I have been troubleshooting this for a bit, and noticed that my xorg.conf was pretty default.  The Device section did not have any driver listed.   I have been searching for tuning tips for this graphics adaper, but most of tips I find deal with the i810 driver which does not seem to work with my graphics adapter.   I currently have it configured for "intel" driver and a mix of "intel" and "i810" driver options. 

Can someone please point me in the right direction for optimal tuning parameters for this driver, card, and xorg.conf?   I am posting my lspci output and xorg.conf below.   Thank you in advance!

ketchup

```
ketchup@locutus:~$ sudo lspci -kv
[sudo] password for ketchup: 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe980000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc80 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fe940000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [d0] Power Management version 2
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, fast devsel, latency 0
    Memory at fe880000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe938000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Memory behind bridge: fea00000-feafffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Hewlett-Packard Company Device 361a
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Hewlett-Packard Company Device 361a
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe937c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Capabilities: [50] Subsystem: Hewlett-Packard Company Device 361a

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: medium devsel, IRQ 15
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 1507
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information <?>
    Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [13c] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 24-00-0c-ff-ff-2c-05-60
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl


ketchup@locutus:~$ cat /etc/X11/xorg.conf
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
    Identifier    "Intel 945 Graphics Controller"
    Driver        "intel"
    BusID        "PCI:0:2:0"
    VideoRAM    131072
        Option         "XAANoOffscreenPixmaps" "true"
        Option         "MigrationHeuristic" "greedy"
#        Option         "AccelMethod" "XAA"  --- this caused some interesting effects
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
ketchup@locutus:~$
```

---

### Post by pauna on 2009-05-19
> **k3tchup said:**
> Hello everyone, 

I am running Ubuntu 9.04 NBR on my HP mini 1030nr (netbook).   According to lspci output, it comes equipped with an Intel Corporation Mobile 945GME Express Integrated Graphics Controller.   It is using intel_agp / intelfb modules.  My issue is that video peformance is choppy.  I get crappy playback on youtube for example and firefox scrolling is annoyingly choppy.    


Unfortunately Intel graphics and Jaunty are not a good mix right now, there are several issues with that combo.

See [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html) for details and some non-optimal solutions.

---

### Post by k3tchup on 2009-05-19
Thanks for the link.  I managed to improve my graphics performance a bit using the information you provided.  Upgrading to kernel 2.6.30-rc2 and newer Intel drivers actually made things much worse, lol.   However, the mtrr fix made improvements, as well as a few xorg.conf modifications.   It's not perfect, but it works much better than before. I will just wait til the next release, with hopefully better Intel drivers.

---

