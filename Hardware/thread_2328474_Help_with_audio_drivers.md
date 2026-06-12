---
title: "Help with audio drivers"
date: 2016-06-21
forum: Hardware
---

### Post by pierre-lonchampt-4 on 2016-06-21
Dear all,

I am trying to use the crappy asus EB1030 eebox.

Nice in a picture - crappy hardware!

Anyway...
I'm stuck with Ubuntu 12.04 LTS with lernel 3.2.0.96 because of the dreaded cedarview drivers.
Anything more recent than that and I'm stuck at boot :(

I can't get the audio working at all. No audio hardware is found by the OS (ubuntu with Xubuntu-desktop) - i.e. the intel chip is found as a PCI one - but its audio function are not recgonized 

I am trying the method described in there  [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)   but for my version, there is no deb that can be downloaded.
I'm therefore trying to build the deb - but I am lost in translation with the errors in the attachment.
I had already progressed - at first the dpkg build would not even start because it was looking for a DEBIAN folder instead of a debian folder...so I suspect this source has never been tested/debugged - which is WASY above my skills :(

Any help appreciated - either with the deb packaging - or with an alternative way to get my sound card recognized by ubuntu!  THX a lot



```

Marmotte@asus1:~/Desktop/oem-audio-hda-daily-dkms-0.201512111017~ubuntu12.04.1$ sudo aplay -l
aplay: device_list:252: no soundcards found...

```


```
marmotte@asus1:~$ sudo alsa force-reload
[sudo] password for marmotte: 
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).
marmotte@asus1:~$ 


```


```
marmotte@asus1:~/Desktop/oem-audio-hda-daily-dkms-0.201512111017~ubuntu12.04.1$ sudo lspci -v
00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 84a9
    Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 84a9
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at dfd00000 (32-bit, non-prefetchable) [size=1M]
    I/O ports at f0d0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [d0] Power Management version 2
    Capabilities: [b0] Vendor Specific Information: Len=07 <?>
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Kernel driver in use: pvrsrvkm
    Kernel modules: cedarview_gfx

00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 80a00000-80bfffff
    Prefetchable memory behind bridge: 0000000080c00000-0000000080dfffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 83ad
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: dfe00000-dfefffff
    Prefetchable memory behind bridge: 0000000080800000-00000000809fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 83ad
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 80400000-805fffff
    Prefetchable memory behind bridge: 0000000080600000-00000000807fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 83ad
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 80000000-801fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 83ad
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at f060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at f040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at f020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at f000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at dff01000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 83ad

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f0c0 [size=8]
    I/O ports at f0b0 [size=4]
    I/O ports at f0a0 [size=8]
    I/O ports at f090 [size=4]
    I/O ports at f080 [size=16]
    Memory at dff00000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: medium devsel, IRQ 3
    I/O ports at 0800 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 84cd
    Flags: bus master, fast devsel, latency 0, IRQ 44
    I/O ports at e000 [size=256]
    Memory at dfe04000 (64-bit, prefetchable) [size=4K]
    Memory at dfe00000 (64-bit, prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
    Capabilities: [d0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 96-00-00-00-68-4c-e0-00
    Kernel driver in use: r8169
    Kernel modules: r8169


```

---

### Post by Yellow Pasque on 2016-06-21
lspci does not see the audio device, which should be at 00:1b.0 according to: [http://www.linux-hardware-guide.com/fr/2014-04-05-asus-eeebox-eb1030-b003l-pre-installed-ubuntu-2gb-ddr3-32gb-ssd](http://www.linux-hardware-guide.com/fr/2014-04-05-asus-eeebox-eb1030-b003l-pre-installed-ubuntu-2gb-ddr3-32gb-ssd)

So the audio chip may be faulty, or it could be disabled in the BIOS (or perhaps something weird is going on in which case you should look at dmesg for clues). Until lspci sees the device, updating the ALSA module won't get you anywhere.

---

### Post by pierre-lonchampt-4 on 2016-06-21
thanks a lot
i HTOUGHT ABOUT THE bIOS aLREADY -  WILL LOOK BETTER THOUGH

---

