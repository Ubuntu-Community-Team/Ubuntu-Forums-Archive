---
title: "Asus UX431FA- only works with nomodeset"
date: 2019-11-22
forum: Hardware
---

### Post by owenl2 on 2019-11-22
Hello,

I had tried with lots of help to get a version of Ubuntu running on my laptop, the non-dedicated graphics version of the Asus Zenbook UX431FA. 

All youtube videos or forum posts conclude that either try this grub edit, or just update bios the end all be all solution that always works. 

No other grub edit works besides nomodeset, and I did update my bios but it still fails. Nomodeset causes the laptop to be unusable (long boot, external display not supported, no brightness control, laptop doesn’t sleep, p much 0 display controls). 

Has anyone else used this specific model to any avail, or have other suggestions?

---

### Post by oldfred on 2019-11-22
To see your video:
sudo lshw -c display

The nomodeset parameter is normally for nVidia.
If you have nVidia chip, then install the nvidia driver and do not use nomodeset.

Try this one if just Intel video:
 i915.fastboot=1 kernel parameter. Fastboot helps provide a clean, flicker-free Linux boot experience.
New 5.1 kernel will include it by default on Skylake and newer
[https://wiki.archlinux.org/index.php/intel_graphics](https://wiki.archlinux.org/index.php/intel_graphics)

Some other Asus models have needed this parameter:
acpi=off

---

