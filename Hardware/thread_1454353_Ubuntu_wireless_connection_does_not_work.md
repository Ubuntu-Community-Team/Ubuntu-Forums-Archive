---
title: "Ubuntu wireless connection does not work"
date: 2010-04-14
forum: Hardware
---

### Post by mjsilverstri on 2010-04-14
Hi,

I have installed ubuntu 9.10 on my laptop, which has a 802.11 n wireless card. 
But I can't get any wireless connection. But when i connected it to a wired network. It works.

Can you please help me with my problem?

Thank you.

---

### Post by ultiva on 2010-04-14
Do you expect to find pixies on this forum ? Post ifconfig, lspci, lsmod and dmesg output here to let people know what hardware do you have and what system is trying to do with it. Also tell us what sort of laptop is this.

---

### Post by dave2001 on 2010-04-14
Very gracious of you Ultiva. As a relative newcommer to Linux myself, I can say that perhaps silversti does not yet know of how much fun obfuscated terminal code can be.

If essence though, you are correct, we need more information. Please post your computer specs, the manufacturer and model of the wireless card, and any error messages you get. You can check out the wireless troublshooting page in the Ubuntu Documentation to learn some of the terminal commands needed to diagnose wireless problems. However, before possibly wasting more time on this, you can check this link to see if Ubuntu supports your wireless card:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

If it's not supported, you might just want to spring for a new card that is.

---

### Post by mjsilverstri on 2010-04-15
Thank you. This is the output of 'lspci -v'. But i dont' know which one is my wireless card. And what to do next. Please help.

> 
0:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: fast devsel
    Capabilities: <access denied>

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (re
v 11)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: d2000000-d30fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Re
gisters (rev 11)
    Subsystem: Device 003c:005c
    Flags: fast devsel
    Capabilities: <access denied>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratc
hpad Registers (rev 11)
    Subsystem: Device 003c:005c
    Flags: fast devsel
    Capabilities: <access denied>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and S
tatus Registers (rev 11)
    Subsystem: Device 003c:005c
    Flags: fast devsel
    Capabilities: <access denied>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Regist
ers (rev 11)
    Subsystem: Device 003c:005c
    Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
    Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Prot
ocol Registers (rev 11)
    Flags: fast devsel

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enha
nced Host Controller (rev 05) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at db105c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Defini
tion Audio (rev 05)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at db100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express R
oot Port 1 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: da100000-db0fffff
    Prefetchable memory behind bridge: 00000000d3100000-00000000d40fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express R
oot Port 2 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: d9100000-da0fffff
    Prefetchable memory behind bridge: 00000000d4100000-00000000d50fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express R
oot Port 5 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d8100000-d90fffff
    Prefetchable memory behind bridge: 00000000d5100000-00000000d60fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express R
oot Port 8 (rev 05)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=08, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: d7100000-d80fffff
    Prefetchable memory behind bridge: 00000000d6100000-00000000d70fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enha
nced Host Controller (rev 05) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, medium devsel, latency 0, IRQ 21
    Memory at db105800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 
01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Cont
roller (rev 05)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port S
ATA AHCI Controller (rev 05) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 34
    I/O ports at 7048 [size=8]
    I/O ports at 7054 [size=4]
    I/O ports at 7040 [size=8]
    I/O ports at 7050 [size=4]
    I/O ports at 7020 [size=32]
    Memory at db105000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (
rev 05)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: medium devsel, IRQ 5
    Memory at db106000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 7000 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation Device 0a2d (rev a2)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 6000 [size=128]
    Expansion ROM at d3080000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel modules: nvidiafb

01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0, IRQ 5
    Memory at d3000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation Device 4239 (rev 35)
    Subsystem: Intel Corporation Device 1311
    Flags: bus master, fast devsel, latency 0, IRQ 36
    Memory at da100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI E
xpress Gigabit Ethernet controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0, IRQ 35
    I/O ports at 4000 [size=256]
    Memory at d4104000 (64-bit, prefetchable) [size=4K]
    Memory at d4100000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at d4110000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
 (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d8100000 (32-bit, non-prefetchable) [size=2K]
    Memory at d8100d00 (32-bit, non-prefetchable) [size=128]
    Memory at d8100c80 (32-bit, non-prefetchable) [size=128]
    Memory at d8100c00 (32-bit, non-prefetchable) [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d8100b00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
 (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: fast devsel, IRQ 16
    Memory at d8100a00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: sdhci-pci

04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d8100900 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at d8100800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Gen
eric Non-Core Registers (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture Sys
tem Address Decoder (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er Target Address Decoder (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er Test Registers (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er Channel 0 Control Registers (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er Channel 0 Address Registers (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er Channel 0 Rank Registers (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er Channel 0 Thermal Control Registers (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er Channel 1 Control Registers (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er Channel 1 Address Registers (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er Channel 1 Rank Registers (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0

ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controll
er Channel 1 Thermal Control Registers (rev 04)
    Subsystem: Hewlett-Packard Company Device 365c
    Flags: bus master, fast devsel, latency 0



---

### Post by ultiva on 2010-04-15
Looks like this entry describes your wifi card:
```

02:00.0 Network controller: Intel Corporation Device 4239 (rev 35)
Subsystem: Intel Corporation Device 1311
Flags: bus master, fast devsel, latency 0, IRQ 36
Memory at da100000 (64-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel driver in use: iwlagn
Kernel modules: iwlagn

```

According to this: [https://bugs.launchpad.net/ubuntu/+source/linux-ports-meta/+bug/520459]("https://bugs.launchpad.net/ubuntu/+source/linux-ports-meta/+bug/520459")

and this: [http://art.ubuntuforums.org/showthread.php?p=8840435]("http://art.ubuntuforums.org/showthread.php?p=8840435")

Your hardware is "Intel Centrino Advanced-N 6200 AGN" and to get it running you should install package linux-backports-modules-karmic-generic and it should work (reboot your computer after installation). Do it and tell if it helps.

Regards

---

### Post by eaglemystic69 on 2010-04-15
Hi, 
Any chance there is hope for me too.  Ive gone back to Jaunty after Karmic insanity.  From my research my driver is not supported.  Got ndiswrapper updated, WiFi light comes on, though no network ever shows in network manager.  

My output is below.  Thank U



sudo lshw -C network

  *-network UNCLAIMED     
       description: Network controller
       product: WiFi Link 100 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:7e:54:8d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.2 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9a:d4:19:a1:b5:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

=================================================================

sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Intel Corporation WiFi Link 100 Series
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

=================================================================

sudo lsmod
Module                  Size  Used by
usblp                  20224  0 
i915                   67844  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
microcode              22036  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         436148  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
uvcvideo               63368  0 
snd_pcm                83076  3 snd_hda_intel,snd_pcm_oss
compat_ioctl32          9344  1 uvcvideo
video                  25872  0 
iTCO_wdt               19108  0 
iwlagn                102788  0 
psmouse                61972  0 
snd_timer              29704  1 snd_pcm
snd                    62756  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
iTCO_vendor_support    11652  1 iTCO_wdt
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
iwlcore               112768  1 iwlagn
lbm_cw_mac80211       227492  2 iwlagn,iwlcore
led_class              12036  1 iwlcore
pcspkr                 10496  0 
serio_raw              13444  0 
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
lbm_cw_cfg80211        73888  3 iwlagn,iwlcore,lbm_cw_mac80211
r8169                  40836  0 
mii                    13312  1 r8169
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
compcache              12876  1 
lzo_decompress         10880  1 compcache
lzo_compress           10880  1 compcache
tlsf                   14092  1 compcache


=================================================================

---

### Post by ultiva on 2010-04-15
Hmmm....

Here it's said [https://lists.ubuntu.com/archives/ubuntu-users/2010-March/213533.html]("https://lists.ubuntu.com/archives/ubuntu-users/2010-March/213533.html") that your card is supported by iwlagn driver. Have you tried to find out why it does not work with this module ? Check out dmesg | grep iwlagn for more info. Also if your try to load ndiswrapper you should blacklist iwlagn and reboot - according to lsmod you provided this module is loaded.

Provide more details. Your Wifi works with ndiswrapper under 9.04 but don't work under 9.10 ? What about 10.04 ? Have you tried livecd ?

---

### Post by mjsilverstri on 2010-04-15
Thank you. I did 'sudo apt-get install linux-backports-modules-karmic-generic' and then reboot my laptop. It does not help. I left-click the network icon in the notification area, it said 'Wireless Network->Device not ready'.

Thank you for any more help.

---

### Post by ultiva on 2010-04-15
> **mjsilverstri said:**
> Thank you. I did 'sudo apt-get install linux-backports-modules-karmic-generic' and then reboot my laptop. It does not help. I left-click the network icon in the notification area, it said 'Wireless Network->Device not ready'.

Thank you for any more help.

Dump here output of command:
dmesg | grep iwlagn

---

### Post by mjsilverstri on 2010-04-15
I have tried 
> 
sudo apt-get install linux-backports-modules-karmic-generic
sudo rmmod -f iwlagn
sudo modprobe iwlagn

> 
$ dmesg | grep iwlagn
[   16.551480] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   16.551483] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   16.551592] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.551620] iwlagn 0000:02:00.0: setting latency timer to 64
[   16.551687] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 6000 Series 2x2 AGN REV=0x74
[   16.585169] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   16.585263] iwlagn 0000:02:00.0: irq 36 for MSI/MSI-X
[   19.273847] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   19.322557] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   19.322562] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   19.325263] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   19.325268] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   19.327622] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[   19.327626] iwlagn 0000:02:00.0: Could not read microcode: -2
[   21.715374] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   21.717767] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   21.717773] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   21.720549] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   21.720555] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   21.723212] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[   21.723217] iwlagn 0000:02:00.0: Could not read microcode: -2
[  499.972889] iwlagn 0000:02:00.0: PCI INT A disabled
[  508.531110] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[  508.531113] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[  508.531487] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  508.531500] iwlagn 0000:02:00.0: setting latency timer to 64
[  508.531553] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 6000 Series 2x2 AGN REV=0x74
[  508.554389] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  508.554473] iwlagn 0000:02:00.0: irq 36 for MSI/MSI-X
[  508.562868] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[  508.565508] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[  508.565513] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[  508.568130] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[  508.568136] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[  508.571438] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[  508.571444] iwlagn 0000:02:00.0: Could not read microcode: -2
[  508.573303] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-3.ucode
[  508.575794] iwlagn 0000:02:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[  508.575801] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-2.ucode
[  508.578351] iwlagn 0000:02:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[  508.578356] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-6000-1.ucode
[  508.580993] iwlagn 0000:02:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2
[  508.580998] iwlagn 0000:02:00.0: Could not read microcode: -2



---

### Post by ultiva on 2010-04-15
Looks like the driver is complaining about firmware it finds. Here is post from someone who had similar problem and his solution.
[http://ubuntuforums.org/showpost.php?p=8840435&postcount=8]("http://ubuntuforums.org/showpost.php?p=8840435&postcount=8")
Post info if it helps.

Also please check if you have this file: iwlwifi-6000-2.ucode on your disk. I suppose it's part of this backport wireless package.

---

### Post by mjsilverstri on 2010-04-15
Where should i look for this file:
 iwlwifi-6000-2.ucode 

Thank you.

---

### Post by mjsilverstri on 2010-04-15
I have looked at this post 'http://ubuntuforums.org/showpost.php?p=8840435&postcount=8' 
But I did see this command completes successfully.

sudo apt-get install linux-backports-modules-karmic-generic

---

### Post by ultiva on 2010-04-15
OK. I found that your module is part of compat-wireless. So you will have to try to compile compat-wireless on your system. This way you'll get newest iwlagn module. Here is how:

1. You have to get compat-wireless snapshot
 a. [http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download") - section "Where to download bleeding edge"
 
 b. if you have problem with compiling this, you may try snapshot from my server (5 April 2010) - this one compiles on my Ubuntu, others doesn't.
 [http://sonylaptop.deimos.org.pl/compat-wireless-2.6.tar.bz2]("http://sonylaptop.deimos.org.pl/compat-wireless-2.6.tar.bz2")

2. Install package build-essential
3. Unpack driver using command: tar -jxvf compat-wireless-2.6.tar.bz2
4. enter newly created directory and type: 
./scripts/driver-select iwlwifi
if no errors then type: make
if no errors then type: sudo make install
just to be certain: sudo depmod -a
5. reboot

Remember that if this works you will have to be careful because upgrading your kernel will blow up wifi and you will have to compile driver again beginning from "make clean".

Ps. I've tried to compile on my Ubuntu driver dated 5 April 2010 using your settings (iwlwifi) and it went OK so You should have no problems.

Regards

---

### Post by mjsilverstri on 2010-04-15
Thank you. This link does not work.
[http://sonylaptop.deimos.org.pl/compat-wireless-2.6.tar.bz2](http://sonylaptop.deimos.org.pl/compat-wireless-2.6.tar.bz2)

And there is compile error when I try the bleeding edge build from #1.

---

### Post by mjsilverstri on 2010-04-15
Thanks A LOT. It works. I went to the archieve of the site and download 4/5 version of the drive. And I followed your steps and now it works.

Thank you very much.

---

### Post by ultiva on 2010-04-16
Sorry for error in the link. I've corrected it on my side in case someone need it. Good to hear that your wifi now works.

---

### Post by dave2001 on 2010-04-20
Very thorough troubleshooting Ultiva, my hat's off.

For anyone else who runs across this thread with similar wi-fi issues, there is another option. If you don't want to hassle with driver/firmware issues that may, or (as in my case) may not work, just buy a new card dirt cheap from e-bay. I got an old Cisco Systems Airo-net 350 card for $9 (shipping included). It was here in 3 days, plugged it in, rebooted, works flawlessly.

---

### Post by thgis05 on 2010-08-26
Thanks ultiva.

Your solution worked.
Had the problem on my Lenovo Thinkpad W510 with ubuntu 9.10 karmic

btw. you can have no spaces in the path to the directory where you unpack compat-wireless. Gave me a make error

---

