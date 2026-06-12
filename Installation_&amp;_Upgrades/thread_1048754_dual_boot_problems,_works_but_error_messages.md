---
title: "dual boot problems, works but error messages"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by PsYcHoTiC_MaDmAn on 2009-01-23
got XP on a 160gb hard drive, set as master
got Ubuntu 8.10 64 on a 20gb hard drive set to slave all on the same IDE cable

should be pretty straightforward, go to boot menu on startup, choose between either of the hard disks to use to boot up from, and it does work.

However I then do get a message on the screen stating "input not supported" which stays on there for about 30seconds, before turning to the standard Ubuntu startup/login screens.

so far cant find any problems (not got around to installing video drivers, going to stick with an ATI card, as that worked well on the other PC (this one) (currently downloading updates (225mb of them))

its not a major problem, but something I'd like to resolve.

---

### Post by Shazaam on 2009-01-23
Do you get the bootup splash screen (orange loading bar) or does it go blank (with the "input not supported" line) and then load up the login screen? If the latter then the screen resolution may be incorrect for the splash screen. Installing drivers for your video card may fix the problem or you can try manually editing menu.lst.

---

### Post by PsYcHoTiC_MaDmAn on 2009-01-24
I'll have a look at that now. hopefully that'll fix it

sounds like what your suggesting

---

### Post by PsYcHoTiC_MaDmAn on 2009-01-24
installed the graphics drivers no luck.

going to /boot/grub/menu.lst I dont see any setting for file resolution

[http://pastebin.com/m38a76ed2](http://pastebin.com/m38a76ed2)

---

### Post by Shazaam on 2009-01-24
Startup-Manager has a setting to change boot resolution. You can get it through Synaptic.

---

