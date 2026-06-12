---
title: "More Xserver problems."
date: 2005-11-27
forum: General Help
---

### Post by HIGHLIFE on 2005-11-27
Ok so I have been trying to install Ubuntu for the fast few weeks on my new computer, but every time I install it some error that says it can not load the xserver comes up.  I have tryed the breezy badger install disc and even the horry hedghog and breezy live discs but nun of them can load the xserver. 

Would this have anything to do with the fact that I have nvidea Geforce 6100 integrated graphics?
It worked in my old computer that had a radeon 9600 in it.

What could I do to fix this?

---

### Post by invalid on 2005-11-27
[QUOTE=HIGHLIFE]Ok so I have been trying to install Ubuntu for the fast few weeks on my new computer, but every time I install it some error that says it can not load the xserver comes up.  I have tryed the breezy badger install disc and even the horry hedghog and breezy live discs but nun of them can load the xserver. 

Would this have anything to do with the fact that I have nvidea Geforce 6100 integrated graphics?
It worked in my old computer that had a radeon 9600 in it.

What could I do to fix this?[/QUOTE]
If you could give us

1) the exact error that you get
2) a copy of your /etc/X11/xorg.conf file

we might could debug.

For now, I can only suggest you install proper drivers for your card (nvidia).
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

This may help,
Cb

---

### Post by RAOF on 2005-11-27
Try the steps above, they should work.

Or, for a fool-proof way to get a (partially) working X server, run
```
sudo dpkg-reconfigure xserver-xorg
``` from the terminal, and select the "vesa" driver when it asks what driver to use (there will be a big list).  Then, leave the default answer for all the other questions unless you know you need something different (like the keyboard question - if you're using an arabic keyboard or something, obviously you don't want to be using the us-104 keyboard keymap :))

---

