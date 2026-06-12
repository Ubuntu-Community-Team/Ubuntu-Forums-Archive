---
title: "Acer asprire 5750G experiences"
date: 2012-03-14
forum: Hardware
---

### Post by Mr.Pytagoras on 2012-03-14
Hi

I'm using (still) ubuntu 11.04 on my acer 5750G and there are some thinks that don't work on this laptop, nor out of the box nor after some configurations. I'm wondering, if somebody who use higher version of ubuntu (11.10 or some 12.04 testing) and have this laptop has any problem with it or if it work out of box?

Thanks

---

### Post by Jujstme on 2012-03-27
This laptop works very well with Ubuntu 11.10, but there are some things that need manual configuration:

- Sound
- LCD Backlight
- Sandy bridge power management
- NVIDIA Optimus VGA

First of all, sound works out of the box but is a bit crappy. To solve this, open /etc/modprobe.d/alsa-base.conf and add this to the bottom of the file:

```
options snd-hda-intel model=auto probe_mask=1

```

Regarding the backlight and the power management problems, edit your boot parameters and add these:

```
acpi_backlight=vendor pcie_aspm=force i915.i915_enable_rc6=1
```

Last but not least, install bumblebee 3.0 or ironhide in order to configure the nvidia card, so you will save battery and your laptop will run cooler, too. Alternatively, if you do not have any intention of using the secondary VGA, you can disable it from BIOS.

---

