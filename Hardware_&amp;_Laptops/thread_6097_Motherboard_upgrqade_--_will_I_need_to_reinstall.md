---
title: "Motherboard upgrqade -- will I need to reinstall?"
date: 2004-11-24
forum: Hardware &amp; Laptops
---

### Post by negativ on 2004-11-24
How good is Ubuntu (or Linux in general) at handling major hardware changes?  I am planning at some point in the near future to go from a motherboard with a VIA KT133 chipset to probably an nForce-based board.  Pretty much everything else (video, sound, drives, etc) will stay the same.

Will I need to reinstall, or will it detect the new stuff and accommodate it appropriately?

---

### Post by bob k on 2004-11-24
[QUOTE=negativ]How good is Ubuntu (or Linux in general) at handling major hardware changes?  I am planning at some point in the near future to go from a motherboard with a VIA KT133 chipset to probably an nForce-based board.  Pretty much everything else (video, sound, drives, etc) will stay the same.

Will I need to reinstall, or will it detect the new stuff and accommodate it appropriately?[/QUOTE]
 I dont know about Ubuntu but I did the same upgrade except from Nvidia to Via in FC2 and during the looking for new hardware it found my new motherboard and hardware and added all of the new drivers.

---

### Post by Burgundavia on 2004-11-24
I recently upgrading from a Via 133 chipset to a Nforce2 one with no problems at all. It even auto detecting/configured onboard sound/ethernet

Now, Win2k, that was another story

Corey

---

### Post by jdong on 2004-11-24
Nope. Ubuntu uses **hotplug** to autodetect ALL your hardware at bootup -- you can switch everything but the hard drive and Ubuntu wouldn't know! LOL

---

