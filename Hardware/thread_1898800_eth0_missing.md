---
title: "eth0 missing"
date: 2011-12-22
forum: Hardware
---

### Post by kemoba on 2011-12-22
On Toshiba P100-415 there is no eth0 interface in iwconfig, i cant connect to internet, i have tried like a million of dmesg commands, lspci commands, but neither shows my Ethernet card.. I`m running Oneiric Ocelot 11.10

iwconfig -a #
```

lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  wlan0     Link encap:Ethernet  HWaddr 00:18:de:bb:c5:c2             inet addr:192.168.26.102  Bcast:192.168.255.255  Mask:255.255.0.0           inet6 addr: fe80::218:deff:febb:c5c2/64 Scope:Link           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:15354 errors:0 dropped:0 overruns:0 frame:0           TX packets:717 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:1689468 (1.6 MB)  TX bytes:144718 (144.7 KB)

```sudo lspci -v

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, fast devsel, latency 0     Capabilities: [e0] Vendor Specific Information: Len=09 <?>  00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])     Flags: bus master, fast devsel, latency 0     Bus: primary=00, secondary=01, subordinate=01, sec-latency=0     I/O behind bridge: 00002000-00002fff     Memory behind bridge: d0000000-d1ffffff     Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff     Capabilities: [88] Subsystem: Toshiba America Info Systems Device ff31     Capabilities: [80] Power Management version 2     Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-     Capabilities: [a0] Express Root Port (Slot+), MSI 00     Capabilities: [100] Virtual Channel     Capabilities: [140] Root Complex Link     Kernel driver in use: pcieport     Kernel modules: shpchp  00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)     Subsystem: Toshiba America Info Systems AC97 Data Fax SoftModem with SmartCP     Flags: bus master, fast devsel, latency 0, IRQ 44     Memory at d2400000 (64-bit, non-prefetchable) [size=16K]     Capabilities: [50] Power Management version 2     Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+     Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00     Capabilities: [100] Virtual Channel     Capabilities: [130] Root Complex Link     Kernel driver in use: HDA Intel     Kernel modules: snd-hda-intel  00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])     Flags: bus master, fast devsel, latency 0     Bus: primary=00, secondary=02, subordinate=02, sec-latency=0     I/O behind bridge: 00006000-00006fff     Memory behind bridge: 84700000-848fffff     Prefetchable memory behind bridge: 0000000084900000-0000000084afffff     Capabilities: [40] Express Root Port (Slot+), MSI 00     Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-     Capabilities: [90] Subsystem: Toshiba America Info Systems Device ff31     Capabilities: [a0] Power Management version 2     Capabilities: [100] Virtual Channel     Capabilities: [180] Root Complex Link     Kernel driver in use: pcieport     Kernel modules: shpchp  00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])     Flags: bus master, fast devsel, latency 0     Bus: primary=00, secondary=03, subordinate=03, sec-latency=0     I/O behind bridge: 00005000-00005fff     Memory behind bridge: 84000000-840fffff     Prefetchable memory behind bridge: 0000000084500000-00000000846fffff     Capabilities: [40] Express Root Port (Slot+), MSI 00     Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-     Capabilities: [90] Subsystem: Toshiba America Info Systems Device ff31     Capabilities: [a0] Power Management version 2     Capabilities: [100] Virtual Channel     Capabilities: [180] Root Complex Link     Kernel driver in use: pcieport     Kernel modules: shpchp  00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])     Flags: bus master, fast devsel, latency 0     Bus: primary=00, secondary=04, subordinate=04, sec-latency=0     I/O behind bridge: 00004000-00004fff     Memory behind bridge: 84100000-842fffff     Prefetchable memory behind bridge: 0000000084300000-00000000844fffff     Capabilities: [40] Express Root Port (Slot+), MSI 00     Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-     Capabilities: [90] Subsystem: Toshiba America Info Systems Device ff31     Capabilities: [a0] Power Management version 2     Capabilities: [100] Virtual Channel     Capabilities: [180] Root Complex Link     Kernel driver in use: pcieport     Kernel modules: shpchp  00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, medium devsel, latency 0, IRQ 23     I/O ports at 1800 [size=32]     Kernel driver in use: uhci_hcd  00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, medium devsel, latency 0, IRQ 19     I/O ports at 1820 [size=32]     Kernel driver in use: uhci_hcd  00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, medium devsel, latency 0, IRQ 18     I/O ports at 1840 [size=32]     Kernel driver in use: uhci_hcd  00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, medium devsel, latency 0, IRQ 16     I/O ports at 1860 [size=32]     Kernel driver in use: uhci_hcd  00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, medium devsel, latency 0, IRQ 23     Memory at d2404000 (32-bit, non-prefetchable) [size=1K]     Capabilities: [50] Power Management version 2     Capabilities: [58] Debug port: BAR=1 offset=00a0     Kernel driver in use: ehci_hcd  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])     Flags: bus master, fast devsel, latency 0     Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32     I/O behind bridge: 00003000-00003fff     Memory behind bridge: d2000000-d20fffff     Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff     Capabilities: [50] Subsystem: Toshiba America Info Systems Device ff31  00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, medium devsel, latency 0     Capabilities: [e0] Vendor Specific Information: Len=0c <?>     Kernel modules: leds-ss4200, iTCO_wdt, intel-rng  00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19     I/O ports at 01f0 [size=8]     I/O ports at 03f4 [size=1]     I/O ports at 0170 [size=8]     I/O ports at 0374 [size=1]     I/O ports at 18b0 [size=16]     Capabilities: [70] Power Management version 2     Kernel driver in use: ata_piix  00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)     Subsystem: Toshiba America Info Systems Device ff31     Flags: medium devsel, IRQ 11     I/O ports at 18c0 [size=32]     Kernel modules: i2c-i801  01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce Go 7900 GS] (rev a1) (prog-if 00 [VGA controller])     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, fast devsel, latency 0, IRQ 16     Memory at d1000000 (32-bit, non-prefetchable) [size=16M]     Memory at c0000000 (64-bit, prefetchable) [size=256M]     Memory at d0000000 (64-bit, non-prefetchable) [size=16M]     I/O ports at 2000 [size=128]     Expansion ROM at <unassigned> [disabled]     Capabilities: [60] Power Management version 2     Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+     Capabilities: [78] Express Endpoint, MSI 00     Capabilities: [100] Virtual Channel     Capabilities: [128] Power Budgeting <?>     Kernel driver in use: nvidia     Kernel modules: nvidia_current, nouveau, nvidiafb  03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)     Subsystem: Intel Corporation Device 1041     Flags: bus master, fast devsel, latency 0, IRQ 45     Memory at 84000000 (32-bit, non-prefetchable) [size=4K]     Capabilities: [c8] Power Management version 2     Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+     Capabilities: [e0] Express Legacy Endpoint, MSI 00     Capabilities: [100] Advanced Error Reporting     Capabilities: [140] Device Serial Number 00-18-de-ff-ff-bb-c5-c2     Kernel driver in use: iwl3945     Kernel modules: iwl3945  0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, medium devsel, latency 168, IRQ 17     Memory at d2004000 (32-bit, non-prefetchable) [size=4K]     Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176     Memory window 0: 80000000-83fff000 (prefetchable)     Memory window 1: 88000000-8bfff000     I/O window 0: 00003000-000030ff     I/O window 1: 00003400-000034ff     16-bit legacy interface ports at 0001     Kernel driver in use: yenta_cardbus     Kernel modules: yenta_socket  0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, medium devsel, latency 64, IRQ 17     Memory at d2006000 (32-bit, non-prefetchable) [size=2K]     Memory at d2000000 (32-bit, non-prefetchable) [size=16K]     Capabilities: [44] Power Management version 2     Kernel driver in use: firewire_ohci     Kernel modules: firewire-ohci  0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, medium devsel, latency 64, IRQ 17     Memory at d2005000 (32-bit, non-prefetchable) [size=4K]     Capabilities: [44] Power Management version 2     Kernel driver in use: tifm_7xx1     Kernel modules: tifm_7xx1  0a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)     Subsystem: Toshiba America Info Systems Device ff31     Flags: bus master, medium devsel, latency 64, IRQ 17     Memory at d2006800 (32-bit, non-prefetchable) [size=256]     Capabilities: [80] Power Management version 2     Kernel driver in use: sdhci-pci               Kernel modules: sdhci-pci

```sudo lsusb

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI

```cat /etc/network/interfaces

```

auto lo iface lo inet loopback

```
dmesg|egrep 'eth0|wlan0|ath0|ra0'

```

[   28.308130] ADDRCONF(NETDEV_UP): wlan0: link is not ready [   37.247114] wlan0: authenticate with 00:21:86:ec:ca:6a (try 1) [   37.249426] wlan0: authenticated [   37.252652] wlan0: associate with 00:21:86:ec:ca:6a (try 1) [   37.256564] wlan0: RX AssocResp from 00:21:86:ec:ca:6a (capab=0x431 status=0 aid=1) [   37.256567] wlan0: associated [   37.258101] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready [   47.408015] wlan0: no IPv6 routers present

```

cat /etc/udev/rules.d/70-persistent-net.rules
```

# This file was automatically generated by the /lib/udev/write_net_rules # program, run by the persistent-net-generator.rules rules file. # # You can modify it, as long as you keep each rule on a single # line, and change only the value of the NAME= key.  # PCI device 0x8086:0x4222 (iwl3945) SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:18:de:bb:c5:c2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"  # USB device 0x0bb4:0x0b28 (usb) SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="80:00:60:0f:e8:00", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"  # PCI device 0x8086:0x109a (e1000e) SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:36:96:e9:29", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"  # PCI device 0x1814:0x0201 (rt2500pci) SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:c0:b7:28:8c:98", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

```

---

### Post by kemoba on 2011-12-23
Bump

---

### Post by collisionystm on 2011-12-23
can you post the entire output of lspci

---

### Post by Bucky Ball on 2011-12-23
> **collisionystm said:**
> can you post the entire output of lspci

+1, but what OP has posted is possibly it. So you are online with another machine and can't get online with cable or wireless on the Tosh?

---

### Post by kemoba on 2011-12-24
I can get on with wireless, but wired will not work, it doesn`t even detect that the cable has been plugged on, so i`m thinking this is a driver problem...
Here is the output of lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce Go 7900 GS] (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

---

### Post by collisionystm on 2011-12-24
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)



So I see wireless but no NIC card.

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)


Note: The iwlwifi driver has been merged into mainline kernel since 2.6.24. If you are using kernels after this release, please use the intree (drivers/net/wireless/iwlwifi) driver directly.


If you are running 11.10 you have the intel driver.

post the output of ifconfig

then

post output of rfkill list

---

### Post by Bucky Ball on 2011-12-24
Yea, wireless all good but your ethernet card is not showing. Has it ever worked, like in Windows or another Ubuntu install? For the ethernet controller, you would be looking for something like this:

```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

Of course the device itself would probably be different to my Realtek one.

---

