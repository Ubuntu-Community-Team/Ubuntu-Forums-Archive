---
title: "Grub &amp; Splash Screen"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by creiss on 2009-09-13
Hey all!  After restoring from backup (everything works) the splash screen past the grub loader are gone. I read about some UIDs and stuff but ugh... Something easier? I tried everything, but cant get the splash screen back to work, instead I see a text-only luks key question and the logging console.  Anyone who can help me get the (standard) ubuntu splash back is my friend ;)  -Chris

---

### Post by creiss on 2009-09-14
bump :*)

---

### Post by creiss on 2009-09-17
OK I am closing in on this one... Seems the standard splash screen is gone:

```

root@hephaestus:~# update-grub 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-15-generic
Updating /boot/grub/menu.lst ... done

```

So, where is the default grub splash screen located?
Cheers!
-Chris.

---

