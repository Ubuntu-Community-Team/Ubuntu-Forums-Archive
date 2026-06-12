---
title: "netgear wireless"
date: 2005-12-19
forum: Hardware &amp; Laptops
---

### Post by treehopper29 on 2005-12-19
I'm a noob to lynex and have a both a netgear router and wireless card i just need a step by step how to on setting up my wireless. thanx

router:MR814V2
card:32bit PCI WG311

---

### Post by Lambert on 2005-12-19
wg311 uses various chipsets so the steps will vary depending on that.

1. Try to go into system>administration>networking . If you see your device in the list then there is a driver loaded for the device. Try to configure and activate. If not in list then you'll probably need to use something called ndiswrapper to get the windows drivers to work.
2. Post back the output of these commands (run from terminal)

```
lscpi -v

sudo lshw -C network
```
3. Also include information about your network setting. Open or encrypted? if encrypted wep or wpa

---

### Post by treehopper29 on 2005-12-19
lspci -v
0000:00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
        Subsystem: ALi Corporation ALI M1541 Aladdin V/V+ AGP System Controller
        Flags: bus master, slow devsel, latency 32
        Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, slow devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: e4000000-e7ffffff

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at eb023000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV] (rev c3)
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:08.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 43)
        Subsystem: D-Link System Inc DFE-530TX rev A
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at e000 [size=256]
        Memory at eb022000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at ea000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:00:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Netgear: Unknown device 4c00
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at eb020000 (32-bit, non-prefetchable) [size=8K]
        Memory at eb000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <available only to root>

0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c2) (prog-if fa)
        Flags: bus master, medium devsel, latency 32
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Magnum/Xpert128/X99/Xpert2000
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        I/O ports at d000 [size=256]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

and

lshw -c
Hardware Lister (lshw) - B.02.03
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

---

### Post by Lambert on 2005-12-20
Your card has a TI chipset which uses the acx111 driver. There's one in breezy but cards do not work out of the box for this. You can search for acx111 in the forums to find success stories. Many of them have gone to this link to get their card working.

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

---

