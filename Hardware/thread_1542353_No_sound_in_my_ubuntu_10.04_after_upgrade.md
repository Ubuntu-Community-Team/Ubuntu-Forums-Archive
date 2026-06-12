---
title: "No sound in my ubuntu 10.04 after upgrade"
date: 2010-07-30
forum: Hardware
---

### Post by rohit.rohan09 on 2010-07-30
I just upgraded my system from Ubuntu 9.10 to Ubuntu 10.04.

With the earlier version the sound was working fine but now I am having problems. I am getting a sound but only from the headphone after i plug its jack in. Else, from the laptop speakers, there is no sound. 

Please help fast as in a few days i will be travelling and will not be connected to the internet for sometime :(

For reference:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dmesg | grep HDA
[   14.345645] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.345724] HDA Intel 0000:00:1b.0: irq 27 for MSI/MSI-X
[   14.345766] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.453681] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   14.455189] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   14.455274] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   14.455347] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13


lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, fast devsel, latency 0, IRQ 26
    Memory at 91000000 (64-bit, non-prefetchable) [size=1M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 30d0 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, fast devsel, latency 0
    Memory at 91100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Conexant Systems, Inc. Device 5051
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at 92400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 91300000-923fffff
    Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 3080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 3060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 3040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at 92404800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 91200000-912fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 30a0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 25
    I/O ports at 30b8 [size=8]
    I/O ports at 30dc [size=4]
    I/O ports at 30b0 [size=8]
    I/O ports at 30d8 [size=4]
    I/O ports at 3020 [size=32]
    Memory at 92404000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: medium devsel, IRQ 11
    Memory at 92404c00 (32-bit, non-prefetchable) [size=256]
    I/O ports at 3000 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Hewlett-Packard Company Device 137b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 91300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 30d9
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at 1000 [size=256]
    Memory at 91200000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp


Please help.. asap.. will be highly obliged!! :(:(:(:(

---

### Post by lidex on 2010-07-31
Can you post the output of these terminal commands for me please:
```
uname -a
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by rohit.rohan09 on 2010-08-10
Thanks lidex for the response.. actually as metioned earlier, i was travelling so could not reply earlier.. my wifi seems to work as i found out.. only the wifi button keeps irritatingly glowiing on even if its off..
Audio though is still screwed up.. :(

The outputs that you had asked are as follows:

_**uname -a**_
Linux rohit-laptop 2.6.34-020634-generic #020634 SMP Mon May 17 20:34:55 UTC 2010 i686 GNU/Linux

_**dpkg -l | grep "alsa"**_
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                                   0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                           1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
ii  linux-alsa-driver-modules-2.6.32-24-generic    2.6.32-24.201008090500                          Ubuntu-supplied Linux modules for version 2.

_**head -n 1 /proc/asound/card*/codec#***_
Codec: Conexant CX20561 (Hermosa)


Do lemme know if anything else is needed..

---

