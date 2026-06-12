---
title: "how do access a Sata hard drive using an os installed on an IDE."
date: 2008-08-01
forum: General Help
---

### Post by morbid_bean on 2008-08-01
ok so my buddies mobo in his pc is shot after a power outage....he wants to know if his data on hard drive is still salvageable....i have never worked with SATA before so im wondering how i would set up this sata hard drive as a slave on MY pc to see if i could recover his files...my current master in my pc is an IDE...i see 2 sata ports on my mobo...how would i go about doing this?

---

### Post by mc4man on 2008-08-01
It would seem you have 3 choices after hooking it up.
You could boot to bios, find the sata drive, turn it off, and then boot up as normal. I wouldn't think you'd get a grub error and you may or may not see / access the drive.

You could boot up to a gparted boot cd and see if you could remove the boot flag on the sata and then boot up normally.

Or you could just boot up as normal.

Myself I'd start with the first, if not try the second, and if that didn't happen then I'd boot up as normal.


edit; if your gonna fool around your hdds it's always good to have a gparted boot cd and a supergrub boot cd on hand

---

### Post by jocko on 2008-08-01
Just plug it in, power up your computer and make sure the boot order is set to boot from ide.

---

### Post by jimv on 2008-08-01
You don't need to do anything.  Just plug the SATA drive in and boot your computer up.  No software to install, no nothing.  It will just show up and you'll be able to use it.

---

### Post by morbid_bean on 2008-08-01
hooked it all up and its not detected by bios ubuntu or windows xp...
it is getting power i know that much

---

### Post by mc4man on 2008-08-02
> its not detected by bios
maybe go back into bios and look around carefully for a setting to enable sata, sata controllers, something to that effect. Each bios could be different, on mine there's an ide/pata setting where 'enhanced' enables the sata controllers along with ide, 'legacy' for just ide, and another i forgot already. As mentioned by jocko, in the boot order just make sure the ide drive is listed first.

Sata 3.0 drives usually have a jumper to force sata 1.5, maybe also look at that.

---

