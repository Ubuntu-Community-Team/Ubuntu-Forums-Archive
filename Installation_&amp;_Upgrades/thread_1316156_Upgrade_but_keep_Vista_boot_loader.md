---
title: "Upgrade but keep Vista boot loader"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2009-11-05
I have a dual-boot laptop, Vista/Ubuntu 9.04.

When I installed 9.04 I used the "advanced" option to avoid writing over the MBR, thus preserving the Vista boot loader. Then I used EasyBCD to add Ubuntu to Vista's boot system. (I use Vista's boot loader so I can get to Vista's hidden restore partition if needed.)

If I upgrade to Ubuntu 9.10 will it mess up my current boot system? Would it be safer to do a fresh install, using the "advanced" option to prevent changing the MBR? I'm concerned because 9.10 uses grub2.

Edit: I found the answer to my question at [https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview#GRUB%202%20by%20default](https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview#GRUB%202%20by%20default) , item #3.13.

---

