---
title: "Poor performance on dv5, graphic and no wifi."
date: 2009-07-06
forum: Hardware
---

### Post by Zemren on 2009-07-06
Hi everyone, first of im a new Linux user so keep that in mind, i just got sick and tired of windows so i decided to convert and even though my Linux isnt fully functional yet i love it!

HP Pavilion DV5 1037.
Ubuntu 8.10

So to my problems, i experience lack of performance in graphics, lag and owerall slow and when i watch movies in vlc the movie flashes in black.

I cant connect wireless to my router only trough cable, the wireless option is missing.

While surfing firefox ist annoyingly slow, feels like surfing a 56k modem with that delay before anything happens, altough i can easily reach 2mb/s while downloading.

What i have done so far is a benchmark to try the graphic.
QGears2:
Rendering: CPU-based Raster - Test: Gears

26.30795 Frames Per Second
25.214325 Frames Per Second
24.94945 Frames Per Second

Average: 25.49 Frames Per Second

also i tried installing madwifi as suggested in this thread
[http://ubuntuforums.org/showthread.php?t=1125494&highlight=dv5&page=2](http://ubuntuforums.org/showthread.php?t=1125494&highlight=dv5&page=2)
And got these errors
/home/zemren/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/zemren/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/zemren/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/zemren/Desktop/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/zemren/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-14-generic'
make: *** [modules] Error 2

zemren@zemren-laptop:~$ sudo lshw -c network
  ```
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:e6:66:2b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.103 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9a:5a:73:15:bd:39
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I dont know what all this means im just posting info that iwe seen was asked for in other threads regarding the same problems.

I started of with ubuntu 9.04 but had the same problems there, maby even vorse but working wifi, converted to 8.10 after i got the recomendation that it would be best for my laptop.

What do you sugest i should do next?

Thanks in advance, hope i made myself clear.):P

---

### Post by Zemren on 2009-07-12
Well wifi problem was sorted out by installing the linux-backports-modules-interpid package. 

Still no progress on the graphic problems so still need help there.

---

### Post by Ekeluo on 2009-07-12
You haven't given any details on your graphics subsystem.

Run lspci -vnn in terminal and paste output here (use code tags when posting)

---

### Post by Zemren on 2009-07-13
Hi here is the result from lspci -vnn

```
Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d2300000-d23fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: d1300000-d22fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: d1200000-d12fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d2500000-d25fffff
    Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0a.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) [1022:9609]
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
    Memory behind bridge: d1100000-d11fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at 6038 [size=8]
    I/O ports at 604c [size=4]
    I/O ports at 6030 [size=8]
    I/O ports at 6048 [size=4]
    I/O ports at 6010 [size=16]
    Memory at d2408000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397] (prog-if 10)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at d2407000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398] (prog-if 10)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at d2406000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396] (prog-if 20)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at d2408500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd
    Kernel modules: ehci-hcd

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397] (prog-if 10)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2405000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398] (prog-if 10)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at d2404000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd
    Kernel modules: ohci-hcd

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396] (prog-if 20)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at d2408400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd
    Kernel modules: ehci-hcd

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: 66MHz, medium devsel
    Capabilities: <access denied>
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c] (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 6000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp, ata_generic, pata_acpi

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
    I/O behind bridge: 00001000-00001fff

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
    Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
    Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
    Flags: fast devsel
    Capabilities: <access denied>

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
    Flags: fast devsel

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3400 Series [1002:95c4]
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=256]
    Memory at d2300000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at d2320000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx

01:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d2310000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

08:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:137b]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at d1200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k, ath_pci

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    I/O ports at 2000 [size=256]
    Memory at d1010000 (64-bit, prefetchable) [size=4K]
    Memory at d1000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at d1020000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

0a:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technologies, Inc. IEEE 1394 Host Controller [197b:2380] (prog-if 10)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d1100000 (32-bit, non-prefetchable) [size=2K]
    Memory at d1100d00 (32-bit, non-prefetchable) [size=128]
    Memory at d1100c80 (32-bit, non-prefetchable) [size=128]
    Memory at d1100c00 (32-bit, non-prefetchable) [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: ohci1394

0a:00.1 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d1100b00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

0a:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: fast devsel, IRQ 18
    Memory at d1100a00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: sdhci-pci

0a:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d1100900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

0a:00.4 System peripheral [0880]: JMicron Technologies, Inc. xD Host Controller [197b:2384]
    Subsystem: Hewlett-Packard Company Device [103c:3600]
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at d1100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>


```

---

### Post by Zemren on 2009-07-14
minor breaktrough, is i deactivate visual effects i can watch movies but with them activated the movie flashes between picture/black frame.

I guess this has something to do with the drivers but is there anyway i can try other drivers than the ones listed in system/harware drivers? as seen my graphic card is a ati mobility radeon hd 3400.

---

