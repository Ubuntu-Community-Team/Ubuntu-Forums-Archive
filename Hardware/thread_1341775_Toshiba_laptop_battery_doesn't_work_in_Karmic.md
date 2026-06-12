---
title: "Toshiba laptop battery doesn't work in Karmic"
date: 2009-11-30
forum: Hardware
---

### Post by which ones pink on 2009-11-30
Hi guys, I have a Toshiba Satellite L-35, and I have two batteries for it (one the stock Toshiba, the other aftermarket), neither of which work in Karmic.  If I unplug it while it's on, it won't change to battery mode, and freezes almost instantly if I try to do anything.  If I boot it while on battery, I can login, but once again as soon as I move the mouse or something, it freezes, and I have to do a hard restart.
Both of these batteries worked fine in Jaunty, and it's a clean install.

I'm guessing it has something to do with the power manager, as it also has this weird problem where the screen dims after about 10 minutes, no matter what I set it, and even if I go into gconf-editor and change it to like a million seconds or something.

Any help is much appreciated, thanks!

---

### Post by which ones pink on 2009-12-02
Well a little update.  I uninstalled laptop-tools (along with acpi-support, which I guess I don't need lol), and it worked for a bit, but I tried it again today and it doesn't work again, except now it won't even boot past the white Ubuntu logo.

---

### Post by Andy_Dempster on 2009-12-02
My Toshiba Satellite A30-303 hasn't worked since 8.04 but I have now found that with the acpi=off option in the menu.lst it works fine, albeit without any kind of power management but I am working on that!

See [http://ubuntuforums.org/showthread.php?t=935461](http://ubuntuforums.org/showthread.php?t=935461) for info!

Andy_D

---

### Post by which ones pink on 2009-12-02
> **Andy_Dempster said:**
> My Toshiba Satellite A30-303 hasn't worked since 8.04 but I have now found that with the acpi=off option in the menu.lst it works fine, albeit without any kind of power management but I am working on that!

See [http://ubuntuforums.org/showthread.php?t=935461](http://ubuntuforums.org/showthread.php?t=935461) for info!

Andy_D

Thanks for the reply.  However, Karmic doesn't have a menu.lst because it uses Grub2, and the new GRUB config files are completely different.  So I'm still stuck.

---

