---
title: "SB live 24 bit and ubuntu"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by socrates50 on 2005-09-13
Just installed Hoary 5.04 on 1.8 GHz P4 with WinXP for dual-boot system.  SB Live 24-bit PCI sound card has no sound out of it, works fine in XP.  When I go to /proc/asound/card0 it shows an Ensoniq Audio PCI ES 1371. How can I fix this in a simple fashion?  Thanks.

---

### Post by graigsmith on 2005-09-13
unfortunately, the sblive 24 bit doesn't use the regular soundblaster live chip.  it uses a cheaper chip, and does alot of things in software.  it uses software mixing, therefore you would have alot of problems with it.  You should configure your system to use ESD because that card needs to use esd as its software sound mixer.

---

