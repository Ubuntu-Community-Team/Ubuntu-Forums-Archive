---
title: "Getting Wireless internet on Aspire One d257"
date: 2011-08-08
forum: Hardware
---

### Post by Paude on 2011-08-08
Hello all! I'm a complete beginner in all things linux, but I just purchased a shiny new Acer Aspire One d257, and installed the netbook version of unbuntu on it (10.10)  using wubi. I haven't been able to get the wireless to work, sadly. I hooked up via a wired connection and let all the drivers auto-install, and installed the recommended extra drivers, but no dice. I have been attempting to find a solution to this problem, because otherwise I am really loving ubuntu on my netbook so far, but wireless Internet is very much a necessity for me. 

In one of the threads in my google results they recommended I post the results of typing lspci -v into terminal, so here is the output:

lspci -v
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 56180000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 40a0 [size=8]
    Memory at 40000000 (32-bit, prefetchable) [size=256M]
    Memory at 56000000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, fast devsel, latency 0
    Memory at 56100000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at 56200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 55000000-55ffffff
    Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 54000000-54ffffff
    Prefetchable memory behind bridge: 0000000051000000-0000000051ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 53000000-53ffffff
    Prefetchable memory behind bridge: 0000000052000000-0000000052ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 4060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 4040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 4020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 56205000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at 4098 [size=8]
    I/O ports at 40ac [size=4]
    I/O ports at 4090 [size=8]
    I/O ports at 40a8 [size=4]
    I/O ports at 4080 [size=16]
    Memory at 56204000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: medium devsel, IRQ 10
    I/O ports at 4000 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at 3000 [size=256]
    Memory at 50004000 (64-bit, prefetchable) [size=4K]
    Memory at 50000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
    Subsystem: Broadcom Corporation Device 0510
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 54000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 0590
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 53000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>



Any help would be greatly appreciated!

---

### Post by sanjeeva311076 on 2011-12-17
[https://launchpad.net/ubuntu/natty/i386/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu3.2](https://launchpad.net/ubuntu/natty/i386/bcmwl-kernel-source/5.100.82.38+bdcom-0ubuntu3.2)

Try the link above and/or download the binary below:

 [http://launchpadlibrarian.net/76999593/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu3.2_i386.deb](http://launchpadlibrarian.net/76999593/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu3.2_i386.deb)

I also needed the dkms dependency below:

[https://launchpad.net/ubuntu/natty/i386/dkms](https://launchpad.net/ubuntu/natty/i386/dkms)

Didn't seem to need the other listed dependencies.  Downloaded the binaries via my windows partition (using karmic koala in a triple boot with android and windows 7) although you could always download them on another computer and transfer via memory stick.  Then copied them to my ubuntu partition - probably doesnt matter where but I copied them into downloads.  Then right-clicked them and opened with GDebi Package Installer (dkms dependency first).  Then rebooted.  Clicked on wireless icon and bob was my uncle.  Unbelievably quick and easy compared to everything I had tried before.  Then had to upgrade kernel before I could update.  Purists would probably know a terminal way to do it but I am far too lazy!

I think I have the same wireless adapter as you - a broadcom 4313 (id 4727 i think)

[U]Learning curve

[/U]1) Probably a slight mistake to install karmic netbook remix - kernel is now 10.04LTS after an upgrade and everything works beautifully (although I haven't tested ethernet yet).  Netbook remix and desktop edition now merged into one apparently.  Not sure if wireless works out of the box with 10.04 though - I'm guessing probably not but I could be wrong.

2) Tried the instructions on the link below first (wrong acer model anyway) but could not install all the listed binaries - dependencies were a pain in the backside especially when trying to install everything (semi)manually.  Might be worth a look if you are still having problems after trying everything above (or if you need to install more dependencies) but seems a roundabout way to do it (especially as you would need to connect to a wired network first assuming you have successfully managed to install a compiler and the ethernet card driver.  I failed miserably.  The instructions also seem to be for an atheros ethernet card rather than your realtek).

[https://help.ubuntu.com/community/AspireOne/AOD255](https://help.ubuntu.com/community/AspireOne/AOD255)

Hope that helps!  First post so apologies for any unintended faux pas.  Feedback or questions welcome but I am a bit of a newb as well so dunno how much help I could be!  Anyway, everything now works and finally enjoying a microsoft-free life!

May the penguin be with you :D

---

### Post by sanjeeva311076 on 2011-12-20
btw forgot to mention bcmwl-kernel is a propietary broadcom driver that seems to work pretty well although I could only find a binary for natty.  Source packages probably available for later kernels though although not sure how easy it will be to compile them.  Didn't bother installing ndiswrapper and didn't seem to need it (but should have expected that since ndiswrapper is for drivers designed for windows I think).

---

