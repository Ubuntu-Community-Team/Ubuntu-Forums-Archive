---
title: "grainy display with intel 82945G/GZ GPU"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by ianare on 2007-06-04
Hi all,

I'm having a weird issue with my dell optiplex gx520 and the intel 82945G/GZ Integrated Graphics. There are many areas where the display is grainy, for example the GNOME splash screen on startup, title bars, highlighting on menu items etc.. If I enable beryl it looks horrible too.

Any ideas?

---

### Post by ramjet_1953 on 2007-06-04
Have you loaded the intel driver?

[COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

After loading, re-boot and see if this has improved things.

Regards,
Roger :cool:

---

