---
title: "Grub error 17"
date: 2008-09-25
forum: General Help
---

### Post by themostunoriginalname on 2008-09-25
I actually kick the power plug and my desktop got its power cut off. When I booted it up, I get a error 17 for Grub.

I loaded up a live CD and tried reloading grub, but that didn't work

I rolled the BIOS back to manufacturer's default, but it didn't work.

menu.lst is nowhere to be found.


This isn't the first time this happened. The last time, I fixed it by loading up the fail-safe and restarted. I can't access the fail-safe this time. How do I access it?

---

### Post by caljohnsmith on 2008-09-25
You probably just need to run an fsck on your Ubuntu partition. Just boot your Live CD and do:
```
sudo fsck -y /dev/sdX
```
Where sdX is your Ubuntu partition. If the hard shutdown you did wasn't to destructive, fsck should be enough to get the Ubuntu partition readable again and thus you won't get a grub error 17.

---

