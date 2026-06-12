---
title: "Grub error 17"
date: 2009-05-21
forum: Hardware
---

### Post by AcidRain0 on 2009-05-21
Hi, I work at a computer repair shop and the other day we had 3 dell dimension's in at the same time, and on each of them I tried booting my flash drive. But on two of them I got grub error 17. And the one just ignored my drive as if I didn't have it plugged in (tried a couple times too) 

I booted my drive by tapping F9 I think for it's bios boot menu, then select "flash drive".

On my flash drive it's a normal ubuntu install except to the flash drive. My flash drive boots on all the other machines and my home computer. Why don't it boot on the dells?

---

### Post by dandnsmith on 2009-05-21
That error sounds like the drive setup on the dell machines isn't the same as your own - the partition number given to grub corresponds to something it cannot handle.

There is a [handy script](https://sourceforge.net/projects/bootinfoscript/) which can trawl the system and tell you what it finds where for booting  - download it and run from within linux, and check the fdifferences in outputs (or possibly post them)

---

