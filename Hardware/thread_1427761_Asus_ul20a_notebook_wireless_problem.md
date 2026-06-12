---
title: "Asus ul20a notebook wireless problem"
date: 2010-03-11
forum: Hardware
---

### Post by staykov on 2010-03-11
I just bought a new Asus ul20a notebook, celeron 1.2 GHz, shrank the win7 partition and installed ubuntu 9.10 64bit. I use linux on laptops for 5 years but now, for first time ever I have a driver problem. The wireless card is not recognized. the cable lan card and the bluethooth work perfectly. I installed linux-backports and linux-backports-wireless as it was suggested on the web but nothing... I tried to compile compat-wireless but I got error msgs. the wireless works perfect on win7.

any help or suggestions will be highly appreciate :) thanks a lot in advance :)

---

### Post by gmc on 2010-03-12
Hi

I picked up an Asus UL20a a few weeks back and don't have any wireless problems. Can you post the ouput from 'lspci -v' and I'll see if I can help get things sorted out for you.

G

---

### Post by staykov on 2010-03-12
thanks for the reply!

the OS is ubuntu 9.10 64bit. I tried also the 32 bit but it was the same. here is the output of lspci -v

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device 1862
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at fe400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at cc00 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: ASUSTeK Computer Inc. Device 1862
    Flags: bus master, fast devsel, latency 0
    Memory at fe800000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at c880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at c800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fe9fbc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 14e3
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fe9f4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at c400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at c000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe9fb800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device 1ea7
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=8]
    I/O ports at b480 [size=4]
    I/O ports at b400 [size=32]
    Memory at fe9fb000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

01:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
    Subsystem: Device 1a3b:1107
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at d800 [size=256]
    Memory at feafc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device 14e5
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

---

### Post by staykov on 2010-03-12
solved!!!

I saw the wireless card model in the output of lspci -v, googled it and found this:
[http://ubuntuforums.org/showpost.php?p=8754255&postcount=5](http://ubuntuforums.org/showpost.php?p=8754255&postcount=5)

followed the instructions there, and it worked!
thank you gmc, wouldn't make it without your help!

---

### Post by gmc on 2010-03-13
HI

Glad to hear you got your wireless working. I noticed something interesting too...

You machine has a Realtek wireless chipset, where as mine is using an Intel chip set..

> 
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8171 (rev 10)
    Subsystem: Device 1a3b:1107
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at d800 [size=256]
    Memory at feafc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
vs mine

> 
01:00.0 Network controller: Intel Corporation WiFi Link 100 Series
        Subsystem: Intel Corporation Device 1305
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Memory at feafe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
I have a couple of questions? What version of Bios are you using? and If you adjust the "Easy Speed" option in the bios from the default 3%, does your screen flicker really badly?

G

---

### Post by staykov on 2010-03-13
I live in Japan and it seems that ASUS have different configurations for different markets. here they sell it only with the celeron CPU but not with the core 2 duo. I changed to 5% but no problems with the screen at all.

---

### Post by gmc on 2010-03-13
Interesting... so it appears not all UL20A's are the same. Near as I can tell my flickering problem seeems to be related to the X.org i915 driver since it's only a problem with linux. Windows 7 doesn't suffer from the same problem.  Thanks for the conformation  G

---

