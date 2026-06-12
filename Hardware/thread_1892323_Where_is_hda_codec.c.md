---
title: "Where is hda codec.c?"
date: 2011-12-07
forum: Hardware
---

### Post by mitchell2.0 on 2011-12-07
I'm trying to compile a driver, following instructions at [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html) and i can't find the file in step 2, hda codec.c
 
I'm using 10.04.3 and I'm trying to get drivers for my modem with the 11c11040 chipset. I also have a modem with the same chipset in my laptop running 11.10, and would like to get both working

---

### Post by bluexrider on 2011-12-07
> **mitchell2.0 said:**
> I'm trying to compile a driver, following instructions at [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html) and i can't find the file in step 2, hda codec.c
 
I'm using 10.04.3 and I'm trying to get drivers for my modem with the 11c11040 chipset. I also have a modem with the same chipset in my laptop running 11.10, and would like to get both working
This file is typically located at [U]/usr/src/linux/sound/pci/hda/hda_codec.c

did you look there
[/U]

---

### Post by bluexrider on 2011-12-07
mine is /usr/sfc/linux_headers-2.6.38-9/sound/pci/hda

---

### Post by mitchell2.0 on 2011-12-07
I looked in both of those locations but didnt find it, search didnt find anything either.

---

