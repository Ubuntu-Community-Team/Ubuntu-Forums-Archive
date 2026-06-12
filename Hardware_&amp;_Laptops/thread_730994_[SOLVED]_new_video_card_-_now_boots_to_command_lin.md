---
title: "[SOLVED] new video card - now boots to command line"
date: 2008-03-21
forum: Hardware &amp; Laptops
---

### Post by spyd3r on 2008-03-21
i recently upgraded from onboard video to an ATI RADEON X600. Now it boots directly to the command line rather than gnome and i cannot 'startx' it tells me something about no screens.  is there a quick fix for this?

---

### Post by Junglizer on 2008-03-21
Try running ```
X -configure
``` from the CLI. Should be that your xorg.conf has not been reconfigured for your new card yet. Once you can successfully launch X, you can change default runlevel in ```
vi /etc/inittab
``` and change the "default runlevel" to 5.

---

### Post by uberlube on 2008-03-21
if you know the address of the new driver you can wget it and install it from the prompt. then a quick restart should fix the problem. Or add vga=791 to the boot process and try booting with that so at least you can get into the desktop.

---

### Post by spyd3r on 2008-03-21
someone else suggested:

sudo dpkg-reconfigure xserver-xorg

---

### Post by spyd3r on 2008-03-23
i'm in my desktop now.  i can't get any of my compiz 3D stuff working now.  I think it's a driver issue, can anyone help with that?

FIX

View this [LINK]("http://paste.ubuntu-nl.org/60735/")

---

