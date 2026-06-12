---
title: "Tip: Grub Error 22 Workaround"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by Jose Catre-Vandis on 2007-01-01
On carrying out a fresh install of Dapper, I got grub Error 22, just getting past Stage1.5 but not getting to the grub boot menu. After several attempts to fix grub (to no avail) I turned to the hardware....

Configuration:

IDE0   HD (Dapper) + CDROM
IDE1   HD + HD (both blank, unformatted)

On removing the IDE1 connector from the motherboard (after switching off!), the system booted. I then tried each hard drive on IDE1 one at a time and the system booted. I put them both back on and the system booted. All drives showed up in "Disks".

So before you start tearing your hair out, it might be something like this.

Error 22 is little documented....

---

### Post by K.Mandla on 2007-01-05
(Moved to Hardware and Laptops. ;) )

Good tip, by the way. :D

---

