---
title: "is there any bluetooth hardware of my laptop ??????"
date: 2015-05-26
forum: Hardware
---

### Post by Hasan55 on 2015-05-26
guy help me........i have managed a laptop so it is new to me. i don't have any idea, is any pci bluetooth hardware contains in this laptop or not?
so plz inform me is any pci bluetooth hardware contains in this laptop????

i gave the command in the terminal to know

root@Hasan5599:~# lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS480 Host Bridge (rev 01)
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI Bridge (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: c0100000-c01fffff
    Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
    Capabilities: [44] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [b0] Subsystem: Hewlett-Packard Company Device 3091

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: ohci-pci

00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (prog-if 10 [OHCI])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0001000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: ohci-pci

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller (prog-if 20 [EHCI])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0002000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [dc] Power Management version 2
    Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: ehci-pci

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 11)
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: 66MHz, medium devsel
    I/O ports at 8400 [size=16]
    Memory at c0003000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [b0] HyperTransport: MSI Mapping Enable- Fixed+
    Kernel driver in use: piix4_smbus

00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 8410 [size=16]
    Capabilities: [70] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: pata_atiixp

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge (prog-if 01 [Subtractive decode])
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=05, subordinate=09, sec-latency=64
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: c0200000-c02fffff
    Prefetchable memory behind bridge: 20000000-23ffffff

00:14.5 Multimedia audio controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: snd_atiixp

00:14.6 Modem: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [40] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: snd_atiixp_modem

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Radeon XPRESS 200M 5955 (PCIE) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
    Memory at c8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 9000 [size=256]
    Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: radeon

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at a000 [size=256]
    Memory at c0208000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too

05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN
    Flags: bus master, fast devsel, latency 64, IRQ 20
    Memory at c0204000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge

05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
    Subsystem: Hewlett-Packard Company Device 3091
    Flags: bus master, medium devsel, latency 168, IRQ 17
    Memory at 24000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
    Memory window 0: 20000000-23ffffff (prefetchable)
    Memory window 1: 28000000-2bffffff
    I/O window 0: 0000a400-0000a4ff
    I/O window 1: 0000a800-0000a8ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus

root@Hasan5599:~# dmesg | grep -i bluetooth
[   19.227270] Bluetooth: Core ver 2.18
[   19.227353] Bluetooth: HCI device and connection manager initialized
[   19.228609] Bluetooth: HCI socket layer initialized
[   19.228622] Bluetooth: L2CAP socket layer initialized
[   19.228655] Bluetooth: SCO socket layer initialized
[   19.268914] Bluetooth: RFCOMM TTY layer initialized
[   19.268937] Bluetooth: RFCOMM socket layer initialized
[   19.268952] Bluetooth: RFCOMM ver 1.11
[   19.270801] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.270808] Bluetooth: BNEP filters: protocol multicast
[   19.270827] Bluetooth: BNEP socket layer initialized
root@Hasan5599:~#

---

### Post by Bucky Ball on 2015-05-26
Please use ```
 tags for terminal output. See the last link in my signature for how.

An easy way to find out is to do a web search for the make/model of your laptop. You don't mention that.

This is telling me you have bluetooth.

[code]root@Hasan5599:~# dmesg | grep -i bluetooth
[ 19.227270] Bluetooth: Core ver 2.18
[ 19.227353] Bluetooth: HCI device and connection manager initialized
[ 19.228609] Bluetooth: HCI socket layer initialized
[ 19.228622] Bluetooth: L2CAP socket layer initialized
[ 19.228655] Bluetooth: SCO socket layer initialized
[ 19.268914] Bluetooth: RFCOMM TTY layer initialized
[ 19.268937] Bluetooth: RFCOMM socket layer initialized
[ 19.268952] Bluetooth: RFCOMM ver 1.11
[ 19.270801] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 19.270808] Bluetooth: BNEP filters: protocol multicast
[ 19.270827] Bluetooth: BNEP socket layer initialized
```

Launch Bluez and see what that tells you. 

Just curious: Why are you running the terminal as root? Better to use 'sudo' in front of your commands and use terminal as your regular user.

---

### Post by jeremy31 on 2015-05-26
It might have bluetooth, I get the same thing in dmesg on a laptop that doesn't have bluetooth.  It is likely that your wifi card has a bluetooth chipset on it.  Post the results from the following
```
lsusb; hciconfig -a; lsmod | grep bluetooth; uname -a
```

---

### Post by Hasan55 on 2015-05-26
hey JEREME31 .....

i have entered your command and my terminal reply me

hasan@Hasan5599:~
$ sudo su -
root@Hasan5599:~# lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0bb4:0003 HTC (High Tech Computer Corp.) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@Hasan5599:~# hciconfig -a
root@Hasan5599:~# lsmod | grep bluetooth
bluetooth             304513  10 bnep,rfcomm
6lowpan_iphc           16548  1 bluetooth
rfkill                 18380  6 y ,hp_wmi,bluetooth
crc16                  12327  2 ext4,bluetooth
root@Hasan5599:~# uname -a
Linux Hasan5599 3.14-0.bpo.2-686-pae #1 SMP Debian 3.14.15-2~bpo70+1 (2014-08-21) i686 GNU/Linux
root@Hasan5599:~# 



NB. MY LAPTOP MODEL NO IS " HP COMPAQ PRESARIO V2000 "
the sceond command nothing reply why ???????? is there any problem or is there any bluetooth adaptor inside of my laptop?????????

---

### Post by Bucky Ball on 2015-05-27
From a very quick search it appears the V2000 series does have bluetooth, but only select models. Look on the bottom of the laptop and get the exact model number (V2000 is the series, not model). As I say, install and launch Bluez (should be installed already and it is what you will be using if you have got bluetooth anyway) and that will soon tell you what you want to know. 

Again, it is not a great idea to become root for EVERY single command you are inputting to the terminal. Definitely not advisable. You appear to favour doing this, but be aware that one false move when you are running as root can severely break your system. Dropping to root for absolutely everything that requires 'sudo' should not be 'rule of thumb'. (For instance, you do not need to be root to run 'lsusb', you don't even need sudo, so you are taking unnecessary so you are leaving yourself open to possible disaster by dropping to root to perform an action that doesn't require it in the first place).

PS: jeremy31 intended for you to enter the whole command I would think, you don't need to break it into segments.

```
lsusb; hciconfig -a; lsmod | grep bluetooth; uname -a
```

Just copy/past that into a terminal and hit enter (NO dropping to root to do it as you don't need to be root.)

Final word: Adventures in the terminal as root permanently when you don't need to be is inviting disaster. End of rant and last word of friendly advice on the matter. ;)

---

### Post by jeremy31 on 2015-05-27
You either don't have bluetooth or it isn't detected by the kernel.  You could buy a USB bluetooth dongle or a wifi/bluetooth card to replace the broadcom wifi if you need to have bluetooth

---

