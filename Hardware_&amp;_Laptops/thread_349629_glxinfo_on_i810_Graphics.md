---
title: "glxinfo on i810 Graphics"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by Desabrir on 2007-01-30
Ok, so Having issues with 3d rendering ... or so I think.

run glx info and I get this warning:

[...]
test@test-desktop:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
[...]

I've read that 3D is only supported on the i810 with a depth of 16 vs the default of 24. I've forced it to 16 and I still get that warning. I used the "sudo dpkg-reconfigure -phigh xserver-org" and chose i810 etc ...

My question is how can I make sure I have the latest and greatest driver for this, and how can fix the libGL warning so that I can do the 3D stuff I'm trying to do. (use WW2D -- [www.ww2d.org](www.ww2d.org))

Desabrir

Edit:

Forgot, running Xubuntu 2.6.17

---

### Post by Desabrir on 2007-01-30
Ok, so I didn't post this in the right section, I just saw hardware and went to town. If I could get someone to move this to the proper topic so I don't cross post and cause a ruckus.

Desabrir

---

