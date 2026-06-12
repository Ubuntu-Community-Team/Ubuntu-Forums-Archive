---
title: "Install new motherboard - reinstall Hoary?"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by fsman on 2005-04-11
I'm swapping out my old motherboard to a Abit KD7A (Via KT400A chipset). Old one was a Asus A7M266 + SoundBlaster.

Will Hoary automatically re-configure to the new motherboard (with new USB2, on-board sound) or do I need to do a clean install?

---

### Post by jdodson on 2005-04-11
[QUOTE=fsman]I'm swapping out my old motherboard to a Abit KD7A (Via KT400A chipset). Old one was a Asus A7M266 + SoundBlaster.

Will Hoary automatically re-configure to the new motherboard (with new USB2, on-board sound) or do I need to do a clean install?[/QUOTE]

it should be fine(might have some xorg problemsm, you can always reconfigure the package).  if it is not fine then do a reinstall.

---

### Post by fsman on 2005-04-11
[QUOTE=jdodson]it should be fine(might have some xorg problemsm, you can always reconfigure the package).  if it is not fine then do a reinstall.[/QUOTE]
 why would I have an xorg problem?

PS - anyone successfuly using the ABIT KD7A?

---

### Post by calvinpriest on 2005-04-11
I replaced my motherboard recently and the only problem I had was my X configuration.  I had to edit xorg.conf, and manually changed the BusID to "PCI:1:0:0", to match the output of lspci.

The relevant lspci output was:
(0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

The "0000:01:00.0" translates to "PCI:1:0:0" in xorg.conf.

I could also presumably have done "sudo dpkg-reconfigure xserver-xorg".

---

