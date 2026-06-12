---
title: "how to force particular driver for touchpad"
date: 2009-09-09
forum: Hardware
---

### Post by Grawp on 2009-09-09
Hi. I have MSI GX720. It has Synaptics touchpad but it's beeing detected as > 00:05 PNP0f03 Microsoft PS/2-style Mouse. I know it because I already tried it with synaptics driver and synclient by editing xorg.conf disallowing empty input and specifing synaptics driver for /dev/input/by-path/pathtomymouse... . However it's not proper way because input devices are managed by HAL (in my case I actually overrode it by allowemptyinput false.. leaving configuration on xorg.conf), but it's not a 'proper' way. Could somebody explain me how to write simple fdi HAL policy file for my case?

---

### Post by Grawp on 2009-09-10
Ok I've already learnt how.

---

