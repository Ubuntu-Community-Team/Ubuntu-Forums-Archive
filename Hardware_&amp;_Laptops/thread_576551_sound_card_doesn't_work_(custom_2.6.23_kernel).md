---
title: "sound card doesn't work (custom 2.6.23 kernel)"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by bushwakko on 2007-10-15
I have installed the 2.6.23-kamikaze2 kernel, which is the 2.6.23-kernel plus some extra patches, not related to alsa as far as I know. The problem is that my soundcard won't work. I've had similar problems on other kernels too. The soundcard did however work after I followed some wiki that did something ubuntu specific with the modules, I have no idea what though, so now that that doesn't work, I have no idea how to fix this. My error is:

[ 1395.109362] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[ 1395.111074] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[ 1395.148319] hda_codec: STAC922x, Apple subsys_id=106b1e00
[ 1395.175656] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 1395.175688] HDA Intel: probe of 0000:00:1b.0 failed with error -16

The important part here seems to be the -16 error

I have a macbook pro, the revision just before santa rosa.

---

