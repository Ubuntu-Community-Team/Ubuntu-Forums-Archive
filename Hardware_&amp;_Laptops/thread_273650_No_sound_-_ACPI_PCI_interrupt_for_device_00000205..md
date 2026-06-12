---
title: "No sound - ACPI: PCI interrupt for device 0000:02:05.0 disabled"
date: 2006-10-08
forum: Hardware &amp; Laptops
---

### Post by rocco_d on 2006-10-08
Hello,

I have Ubuntu 6.06, but I have no sound.

My sound card is Cirrus Logic CS4280 onboard on HP Kayak XM600 workstation (mainboard is asus p3c-d).

It is properly recognized as CS46xx, which according to the ALSA database is what module should be used.

My problem is that all apps as well as ALSA complain that there aren't any sound devices.

>dmesg

[17180599.380000] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 17 (level, low) -> IRQ 201
[17180601.516000] ACPI: PCI interrupt for device 0000:02:05.0 disabled

>lspci | grep 02:05

0000:02:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

Also when the PC boots, right under 'Uncompressing kernel image...'

I get the message (please excuse me if I don't remember it exactly)

PCI: Failed to allocate mem resource for device 6...

My onboard sound card is seen as PCI device 6.

The sound is OK in windows. I thought that maybe I can change something from the BIOS, but it has just a few options. The only ones related (remotely) are PnP OS, reset configuration data, enable onboard sound. I used all 4 possiblities for the first 2, but I always get the same problem.

Please help me sort this out
Thanks,
Rouslan

---

