---
title: "What drivers should I install?"
date: 2016-05-04
forum: Hardware
---

### Post by jorge39 on 2016-05-04
I did ```
lspci -v
``` and the output was:

```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)	Subsystem: Hewlett-Packard Company Device 1967
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>


00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: b6000000-b6ffffff
	Prefetchable memory behind bridge: 00000000b2000000-00000000b2ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:01.1 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x8 Controller (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: b5000000-b5ffffff
	Prefetchable memory behind bridge: 00000000a0000000-00000000b1ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 1967
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at b7000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915


00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
	Subsystem: Hewlett-Packard Company Device 1967
	Flags: bus master, fast devsel, latency 0, IRQ 33
	Memory at b7910000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel


00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05) (prog-if 30 [XHCI])
	Subsystem: Hewlett-Packard Company Device 1967
	Flags: bus master, medium devsel, latency 0, IRQ 26
	Memory at b7900000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd


00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Hewlett-Packard Company Device 1967
	Flags: bus master, fast devsel, latency 0, IRQ 30
	Memory at b7918000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei_me


00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1967
	Flags: bus master, fast devsel, latency 0, IRQ 32
	Memory at b7914000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: b7400000-b76fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0f, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: b4000000-b4ffffff
	Prefetchable memory behind bridge: 00000000b3000000-00000000b3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d5) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: b7800000-b78fffff
	Prefetchable memory behind bridge: 00000000b7700000-00000000b77fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1967
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at b791c000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1967
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: lpc_ich


00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 1967
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at 7088 [size=8]
	I/O ports at 7094 [size=4]
	I/O ports at 7080 [size=8]
	I/O ports at 7090 [size=4]
	I/O ports at 7060 [size=32]
	Memory at b791b000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci


00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1967
	Flags: medium devsel
	Memory at b7919000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 7040 [size=32]


07:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)
	Subsystem: Hewlett-Packard Company Device 21a0
	Flags: fast devsel, IRQ 16
	Memory at b5000000 (32-bit, non-prefetchable) [size=16M]
	Memory at a0000000 (64-bit, prefetchable) [size=256M]
	Memory at b0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 5000 [size=128]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

```

Can anyone help? 

Thanks! :)

---

### Post by Bucky Ball on 2016-05-04
What is the actual problem? Can you be more specific about what drivers you want help with?

On further reading, I can only presume you are talking about the 'access denied' in every hardware component entry so doubt this has anything to do with one specific driver, or drivers at all perhaps. Just to let you know, mine is exactly the same (16.04), so unless you have a specific issue you need to solve or are you just curious about what you're seeing from this command?

But again. Is the machine working fine?

PS: It helps potential helpers immensely if you include your actual question in the thread title or at least somewhere in the first post so we have a clue and don't need to rely on guesswork or wasting time posting back and forth to work out what help you're after. Help us help you. :)

---

### Post by mastablasta on 2016-05-04
my quess is this is the issue:

```
07:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)
 Subsystem: Hewlett-Packard Company Device 21a0
 Flags: fast devsel, IRQ 16

```

```

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06) (prog-if 00 [VGA controller])
 Subsystem: Hewlett-Packard Company Device 1967
 Flags: bus master, fast devsel, latency 0, IRQ 31
 Memory at b7000000 (64-bit, non-prefetchable) [size=4M]
 Memory at c0000000 (64-bit, prefetchable) [size=256M]
 I/O ports at 7000 [size=64]
 Expansion ROM at <unassigned> [disabled]
 Capabilities: <access denied>
 Kernel driver in use: i915

```

though i have to say i didn't know they have Xeons on laptops. isn't that a  server CPU?

In any case if this is optimus PC it will need nvidia drivers. intel GPU drivers are built into kernel, while nvidia opensoruce (while built in) are not as good as the proprietary ones from nvidia.

if this is an optimus system you will also need bumblebee in order to switch between GPU chips. read more here: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by jorge39 on 2016-05-04
Sorry about not being objective :/

The first problem is that whenever I close and reopen the laptop screen it goes directly to lock screen without suspending. 

When I do "sudo pm-suspend" in the terminal it does nothing.

If possible I would also like to have a stronger wifi connection because I notice that in windows I have a stronger wifi connection than in ubuntu (maybe need to upgrade/install other network controller?).

Thank you for the reply!

---

### Post by jorge39 on 2016-05-04
Thank you for the reply mastablasta!

I will read that better and try to do what you suggested. I will come back and say if it helped or not in case someone has the same issue. :)

---

### Post by Bucky Ball on 2016-05-04
> **jorge39 said:**
> The first problem is that whenever I close and reopen the laptop screen it goes directly to lock screen without suspending.

What's it doing when you close the laptop lid if it's not suspending? The screen is staying on with the lid closed? Do you mean you open the laptop lid and you need to login again or you open the lid and it goes to a desktop and the screen is locked, you can't do anything but restart the machine?

> **jorge39 said:**
> If possible I would also like to have a stronger wifi connection because I notice that in windows I have a stronger wifi connection than in ubuntu (maybe need to upgrade/install other network controller?).

This is the stuff of another thread. Please edit it out here and post about it in *Networking and Wireless* to improve your chances of support and avoid confusion as the title, subject and forum of this current thread are unrelated. Thanks.

---

