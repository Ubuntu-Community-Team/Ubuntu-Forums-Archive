---
title: "Thinkpad 600 sound issues..yet another thread.."
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by senkin on 2005-12-03
hey

i wonder what this is about. added snd-cs4236 to /etc/modules and it finds the module and seems to work except for one thing: it wont play audio. at all. i just get hissing out of my speakers so the card works but...

also, tried to put the modprobe settings in /etc/modules and the damn thing stopped working altogether. /etc/modprobe.d/sound needs to have them it seems..anyway. any ideas? i really need the laptop to put out sound.

---

### Post by senkin on 2005-12-03
ha! here's what helped:

root=/dev/hda1 noapic nolapic acpi=off amp=on pnpbios=off ro quiet splash

in the menu.lst

way cool

---

