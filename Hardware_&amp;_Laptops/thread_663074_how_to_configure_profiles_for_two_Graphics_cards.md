---
title: "how to configure profiles for two Graphics cards?"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by linuxd00 on 2008-01-09
hi,
i have a little problem:

i have a Thinkpad X31(gutsy gnome), which has the (agp)Radeon 7000 installed.

i also use it in a docking station which has a PCI ATI RADEON 9200 on it...

when i boot the laptop on the docking station it boots up fine(i even get the loading UBUNTU splash screen so graphics seem to work) just when X has to start it hangs(still in text mode)...

if i change to TTY1 and try to manually start X or any other GUI Application it says something like " screen found but no suitable resolution" or "no screen found"

i think the configuration in the xorg.conf is missing but im afraid to reconfigure it as i dont want to mess with or delete the undocked settings...

is there a way to set a profile(maybe in Grub?) or define those two cards in xorg.conf so that it automatically chooses the needed driver when booting?

thanks for any ideas!

---

