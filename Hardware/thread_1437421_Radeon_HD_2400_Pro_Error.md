---
title: "Radeon HD 2400 Pro Error"
date: 2010-03-23
forum: Hardware
---

### Post by jleppers on 2010-03-23
ok here is the problem, i had a nvidia geforce FX 5700LE and i just replaced it with a Visiontek Radeon HD 2400 Pro, i insatlled all the drivers from the hardware driver detection and installed it and it gave me an error like (EE) No valid frambuffer address. i looked it up on google and found i can use the radeonhd driver from useing the apt-get install command i then edited the xorg.conf file and updated the driver to "radeonhd" now when it boots it says

(II) RADEONHD(0): The detected amount of videoram exceeds the PCI BAR aperture.
(II) RADEONHD(0): Using only 0kB of the total 524288kB.
(EE) RADEONHD(0): No Video RAM detected.
(II) UnloadModule: "radeonhd"
(EE) Screen(s) found, but none have a usable configuration.

---

