---
title: "HP Notebook REINSTALL SOUND? Pulseaudio or Alsa?"
date: 2010-03-20
forum: Hardware
---

### Post by cusinmex on 2010-03-20
Hello forum

My HP Pavilion DV4 notebook has been having problems
with the sound for weeks, and I still haven't been able
to fix it.

I've already looked at some other posts, and tried their
posted solutions, but no luck. :(

Some sites say that pulseaudio is the way to go, 
and others differ by saying stick to alsa.

How do I remove all the sound drivers so that it's
clean, and reinstall alsa?





[HTML]http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio[/HTML]

[HTML]http://ubuntuforums.org/showthread.php?t=789578&highlight=reinstall+sound+jaunty[/HTML]

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
	Subsystem: Hewlett-Packard Company Device 3642
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
	Memory behind bridge: 70000000-700fffff
	Prefetchable memory behind bridge: 0000000091000000-00000000910fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 2298
	I/O ports at 8038 [size=8]
	I/O ports at 804c [size=4]
	I/O ports at 8030 [size=8]
	I/O ports at 8048 [size=4]
	I/O ports at 8010 [size=16]
	Memory at 92508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at 92507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at 92506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at 92508500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 92505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at 92504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at 92508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, slow devsel, latency 0, IRQ 4
	Memory at 92500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 80000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at 92400000 (32-bit, non-prefetchable) [size=64K]
	Memory at 92300000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

01:05.1 Audio device: ATI Technologies Inc Device 970f
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, fast devsel, latency 0, IRQ 7
	Memory at 92410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company Device 3040
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at 91100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, fast devsel, latency 0, IRQ 19
	I/O ports at 2000 [size=256]
	Memory at 91010000 (64-bit, prefetchable) [size=4K]
	Memory at 91000000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at 91020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8101
	Kernel modules: r8101, r8169

```

---

### Post by I8NY on 2010-03-20
to remove the audio drivers and install ALSA(last line) run ```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get purge alsa-base linux-sound-base alsa-utils
sudo apt-get install alsa-base linux-sound-base alsa-utils
```
it should work unless your sound drivers use a different name.

---

### Post by cusinmex on 2010-03-20
> **I8NY said:**
> to remove the audio drivers and install ALSA(last line) run ```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get purge alsa-base linux-sound-base alsa-utils
sudo apt-get install alsa-base linux-sound-base alsa-utils
```
it should work unless your sound drivers use a different name.


The sound still doesn't work, and nothing
appears in the sound menu.

So it must be the sound card?

---

### Post by I8NY on 2010-03-20
if you can still get to the sound preference then you are still running PulseAudio(mine doesn't open with ALSA) and the pulse audio is still installed and that might be interfering with ALSA.  Did you get any errors when removing the audio drivers?

---

### Post by cusinmex on 2010-03-20
> **I8NY said:**
> if you can still get to the sound preference then you are still running PulseAudio(mine doesn't open with ALSA) and the pulse audio is still installed and that might be interfering with ALSA.  Did you get any errors when removing the audio drivers?


I found that weird because i didn't get any errors,
but when i try to open the volume panel, it gives me an
error related to gstreamer..



```
pepelalo@pepelalo-laptop:~$ aplay -l
aplay: device_list:217: no soundcards found...

``` 

so then how do I install the sound card driver or configure it?

---

### Post by I8NY on 2010-03-22
hmm.... was the sound card working before?  You might want to try reinstalling gstreamer in the package manager.

---

### Post by cusinmex on 2010-03-25
nevermind

i upgraded to karmic
and everything works great now.

---

