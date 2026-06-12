---
title: "Odd boot problem"
date: 2008-09-17
forum: General Help
---

### Post by Captain Giraffe on 2008-09-17
My ubuntu 8.04 (server ed.) installation seems to require a soft boot to startup correctly.

If i do a $shutdown -r now , or if I do a power off / power on I cant get past grub. It halts at the "Starting up..." message. 
I edited the grub menu and removed splash quiet, just to try and find whats failing, still not a single message besides the initial "Starting up...".
Nothing in /var/log/dmesg either (none created).

If I do a soft boot (ctrl-alt-del) it works fine. If I fiddle in the grub menu and boot via b option (still booting the default and nothing changed in the options) it also works fine. No suspicious messages or anything.

Fiddling in the GRUB menu is not a viable option since the comp sits in a dark closet with no console attached.
I'm in the dark here too.
Any ideas? anything?

/Captain

---

### Post by Titan8990 on 2008-09-17
Try adding the following to the boot line in GRUB:

acpi=off


If it does not solve your issue then don't forget to remove it.

---

### Post by Captain Giraffe on 2008-09-17
No change on the failing hard/shutdown -r boots, but adding the noacpi line makes the soft boot fail from an interrupt 20 and following io errors. 
Could it really be a boot settings problem? since just fiddling, not changing, in the GRUB menu after a hard boot fixes it.

Also wouldnt a shutdown -r, be more similar to a ctrl-alt-delete rather than power off / on?

---

### Post by Captain Giraffe on 2008-09-19
bumpitybump

---

