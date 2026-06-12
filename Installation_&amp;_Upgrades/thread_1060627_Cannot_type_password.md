---
title: "Cannot type password"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by userkiller on 2009-02-04
i cannot type my password when login in please help.

---

### Post by pauwl on 2009-02-05
I had this once in an older build, turned out to be graphics card related.

I presume your mouse works OK?

Check there is any input possible from keyboard by pressing CTRL+ALT+BACKSPACE. gdm should reboot. (at least we know the keyboard works)

This will at least let you see if your keyboard is working at all or not.

It may be a configuration issue, and you might need to reboot (click "options".."Restart"), and whilst in the GRUB boot menu (you might need to press ESC whilst booting to get there), select (recovery mode).

This will boot you into a recovery menu.
Select "root" from there.
Type: dpkg-reconfigure xserver-org

Go through the steps choosing basic settings.

Reboot & good luck.

---

### Post by userkiller on 2009-02-05
my mouse don't work

---

