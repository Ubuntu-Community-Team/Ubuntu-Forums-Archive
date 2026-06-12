---
title: "Lenovo thinkpad showing nothing under aplay -l"
date: 2013-09-11
forum: Hardware
---

### Post by Chetan_Sanghani on 2013-09-11
Hi 

To start off, I'm sorry to say I am a complete beginner to Ubuntu and am a Windows convert. Recently I have been having an issue where my onboard sound card doesn't show up under the sound settings, all I get is "Dummy Output"

The obvious aim for this post is to see if I can restore sound to my machine.

After some net research, every solution seemed to be from before 2010... so I am stumped. What little I did find out is that  when I look under aplay I get this response

chetan@Chets-Laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****

When I sudo lspci -v I get this :
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    Subsystem: Lenovo ThinkPad T61/R61
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0a <?>
    Kernel driver in use: agpgart-intel


00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c) (prog-if 00 [VGA controller])
    Subsystem: Lenovo ThinkPad T61/R61
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f8000000 (64-bit, non-prefetchable) [size=1M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915


00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
    Subsystem: Lenovo ThinkPad T61/R61
    Flags: bus master, fast devsel, latency 0
    Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: [d0] Power Management version 3


00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
    Subsystem: Lenovo Device 20de
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f8200000 (32-bit, non-prefetchable) [size=128K]
    Memory at f8225000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1840 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: e1000e


00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd


00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T60
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd


00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at f8426c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: ehci-pci


00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Lenovo ThinkPad T61
    Flags: fast devsel, IRQ 17
    Memory at f8220000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link


00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f4000000-f5ffffff
    Prefetchable memory behind bridge: 00000000f8500000-00000000f85fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo ThinkPad T61
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport


00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f6000000-f7ffffff
    Prefetchable memory behind bridge: 00000000f8600000-00000000f86fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: Lenovo ThinkPad T61
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport


00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 18a0 [size=32]
    Kernel driver in use: uhci_hcd


00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 18c0 [size=32]
    Kernel driver in use: uhci_hcd


00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at f8427000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci-pci


00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=08, sec-latency=32
    I/O behind bridge: 00004000-00007fff
    Memory behind bridge: d4000000-d7efffff
    Prefetchable memory behind bridge: 00000000d8000000-00000000dbffffff
    Capabilities: [50] Subsystem: Lenovo ThinkPad T61


00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 03)
    Subsystem: Lenovo T61
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel driver in use: lpc_ich


00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18e0 [size=16]
    Kernel driver in use: ata_piix


00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo ThinkPad T61
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at 1c30 [size=8]
    I/O ports at 1c24 [size=4]
    I/O ports at 1c28 [size=8]
    I/O ports at 1c20 [size=4]
    I/O ports at 1c00 [size=32]
    Memory at f8426000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [80] MSI: Enable+ Count=1/4 Maskable- 64bit-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci


00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Lenovo ThinkPad T61
    Flags: medium devsel, IRQ 11
    Memory at f8427400 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c40 [size=32]


03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Device 1011
    Physical Slot: 3
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7f00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-1f-3b-ff-ff-97-37-9f
    Kernel driver in use: iwl4965


05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
    Subsystem: Lenovo Device 20c6
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at d7eff000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=05, secondary=06, subordinate=07, sec-latency=176
    Memory window 0: d8000000-dbffffff (prefetchable)
    Memory window 1: 80000000-83ffffff
    I/O window 0: 00004000-000040ff
    I/O window 1: 00004400-000044ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus


05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) (prog-if 10 [OHCI])
    Subsystem: Lenovo Device 20c7
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at d7efe800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [dc] Power Management version 2
    Kernel driver in use: firewire_ohci


05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
    Subsystem: Lenovo ThinkPad W500
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at d7efe400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
    Kernel driver in use: sdhci-pci

I don't really know what do from this point onwards, if anyone has any suggestions, that would be grand as I'm at my wits end here.

---

### Post by tgalati4 on 2013-09-11
It should look like:


tgalati4@tpad-Gloria7 ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have an older Thinkpad, T43p, but the sound chip is an Intel ICH6.  Yours is an ICH8.  It's strange that some drivers think your machine is a T60, yet your machine is really a W500.

Was sound working at all, or has it never worked?  It should be plug-and-play with no extra effort on your part.  You can try restarting pulseaudio:

```
pulseaudio -k
```

You will want to spend a little time learning how pulseaudio works:  [http://www.freedesktop.org/wiki/Software/PulseAudio/FAQ/](http://www.freedesktop.org/wiki/Software/PulseAudio/FAQ/)

[http://manpages.ubuntu.com/manpages/hardy/man1/padevchooser.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/padevchooser.1.html)

Check to make sure you have ALSA installed.  It provides the actual modules to handle the sound chips.

```
apt-cache policy alsa-utils
```

The script that actually loads alsa:  /etc/init.d/alsa-utils

It's helpful to go through it and see if you have any issues.

```
cat /var/log/udev
``` will show what hardware is detected and loaded.

---

### Post by Chetan_Sanghani on 2013-09-12
the sound HAS worked in the past, but I don't know when it stopped...

I tried restarting pulseaudio to no avail... and alsa-utils claims its installed. However when i "cat /var/log/udev" I'm seeing references to toshiba EVERYWHERE, just what in the name of seven hells is going on with the drivers here : /

---

### Post by tgalati4 on 2013-09-12
It's possible that your sound chip crapped out and thus udev doesn't recognize it.  Do you have a rescue partition with Lenovo diagnostic utilities?  If you load the diagnostics and the sound doesn't work, then that would be a clue.

Does this machine dual-boot?  Does sound work in Windows?

This is what udev looks like on a newer machine (Acer extensa) with an ICH8 sound chip:

tgalati4@Mint14-Extensa /var/log $ grep toshiba udev
tgalati4@Mint14-Extensa /var/log $ grep TOSHIBA udev
tgalati4@Mint14-Extensa /var/log $ grep INTEL udev
tgalati4@Mint14-Extensa /var/log $ grep intel udev
DRIVER=agpgart-intel
DRIVER=agpgart-intel
KERNEL[31.789567] add      /devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight (backlight)
DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight
KERNEL[32.039894] add      /module/snd_hda_intel (module)
DEVPATH=/module/snd_hda_intel
FIRMWARE=intel-ucode/06-0f-0d
KERNEL[32.800927] add      /bus/pci/drivers/snd_hda_intel (drivers)
DEVPATH=/bus/pci/drivers/snd_hda_intel
UDEV  [32.805155] add      /devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight (backlight)
DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight
UDEV  [32.861141] add      /module/snd_hda_intel (module)
DEVPATH=/module/snd_hda_intel
UDEV  [32.926189] add      /bus/pci/drivers/snd_hda_intel (drivers)
DEVPATH=/bus/pci/drivers/snd_hda_intel
FIRMWARE=intel-ucode/06-0f-0d
FIRMWARE=intel-ucode/06-0f-0d
FIRMWARE=intel-ucode/06-0f-0d
FIRMWARE=intel-ucode/06-0f-0d
FIRMWARE=intel-ucode/06-0f-0d
FIRMWARE=intel-ucode/06-0f-0d
FIRMWARE=intel-ucode/06-0f-0d

No toshiba entries.

---

### Post by Chetan_Sanghani on 2013-09-12
I wussed out and reinstalled, aplay -l shows the controller and sound works, hell, it even recognised as an x61s now, cheers for the help:)

---

