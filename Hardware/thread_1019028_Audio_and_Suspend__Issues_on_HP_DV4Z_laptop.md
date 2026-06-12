---
title: "Audio and Suspend  Issues on HP DV4Z laptop"
date: 2008-12-22
forum: Hardware
---

### Post by Brian2 on 2008-12-22
I just installed Ubuntu 8.10 on my new HP DV4Z laptop and most everything worked right out of the box, except for suspend and audio. I have had no sound what so ever. I have searched long and hard, and nothing I have tried seemed to have fix the issue, still no sound at all. I submitted a bug to ALSA and a hardware report to Launchpad.
This thread covers the same issue, but with no resolution. Just wondering if anyone else has some ideas. Thanks.

[http://ubuntuforums.org/showthread.php?t=973270](http://ubuntuforums.org/showthread.php?t=973270)


The suspend hangs upon awakening. The mouse and keyboard wake the computer up but then it seems to no longer accept any input. My password is requested and I can see the text insert blinking in the entry box, but I am unable to enter text or move the mouse. I am forced to restart to regain control of my laptop. Having a laptop, this is very important to me to get fixed. 

Any direction would be much appreciated. Thanks!

Here is my lspci output:

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: 92300000-924fffff
	Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00006fff
	Memory behind bridge: 91300000-922fffff
	Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: 91200000-912fffff
	Prefetchable memory behind bridge: 0000000070000000-00000000700fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: 91100000-911fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 70100000-701fffff
	Prefetchable memory behind bridge: 0000000091000000-00000000910fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8038 [size=8]
	I/O ports at 804c [size=4]
	I/O ports at 8030 [size=8]
	I/O ports at 8048 [size=4]
	I/O ports at 8010 [size=16]
	Memory at 92508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at 92507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at 92506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at 92508500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 92505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 92504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at 92508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at 92500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=80, subordinate=8f, sec-latency=64
	I/O behind bridge: 00001000-00001fff

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at 92400000 (32-bit, non-prefetchable) [size=64K]
	Memory at 92300000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: ATI Technologies Inc RS780 Azalia controller
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at 92410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

08:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 91200300 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at 70000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: fast devsel, IRQ 17
	Memory at 91200200 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at 91200100 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at 91200000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

09:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Hewlett-Packard Company Device 137c
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 91100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30fb
	Flags: bus master, fast devsel, latency 0, IRQ 219
	I/O ports at 2000 [size=256]
	Memory at 91010000 (64-bit, prefetchable) [size=4K]
	Memory at 91000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at 91020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

---

### Post by Brian2 on 2008-12-24
bump

---

### Post by balak on 2009-01-07
Did you make any progress? We just bought this laptop and I am setting up intrepid.

For me, resume from suspend works if I select suspend from the logout menu but not if the computer automatically suspends (as a result of power management preferences). That could be one clue to the bug.

I think gnome-power-manager calls scripts from 
/usr/lib/hal/scripts/linux - so maybe there is some inconsistency there. I'll take a look in the next few days.

---

### Post by balak on 2009-01-07
Correction: The in-built speakers are not working.

I am able to hear music when I connect headphones to the laptop.
(I haven't made any changes so far)

---

### Post by balak on 2009-02-21
Folks,

The solution is given in
[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)

Basically its fixed in the newest version of alsa but since it will take a few weeks/months for ubuntu to move to that version you will need to install it yourself.

If you are comfortable with doing things in the command line and more importantly keeping track of what you did so that you can repeat it after a kernel upgrade, go ahead as given in the thread above. I have it working on my dv4 perfectly.

---

### Post by andresFang on 2009-03-02
that post works perfect, now i have sound on my CQ45-115LA

---

