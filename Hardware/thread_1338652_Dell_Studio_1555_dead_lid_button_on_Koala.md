---
title: "Dell Studio 1555 dead lid button on Koala"
date: 2009-11-26
forum: Hardware
---

### Post by rengolin on 2009-11-26
Karmic Koala 64-bit fixed the suspend/hibernate problems that 9.04 had. But in the past weeks I can't make the lid do nothing...

I can suspend/hibernate then close the lid, but that's a bit too annoying. I tried running the /etc/acpi/lid.sh but the CheckPolicy returns always false.

gnome-power-manager is running, all settings are good. If I comment out the CheckPolicy line, everything works. I'm guessing there's a mistake somewhere that got lost on one of my upgrades.

Anyone has any idea where to look for?

Thanks!

---

