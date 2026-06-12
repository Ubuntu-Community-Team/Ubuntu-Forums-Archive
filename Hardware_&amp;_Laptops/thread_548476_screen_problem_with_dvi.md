---
title: "screen problem with dvi"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by sotpar on 2007-09-11
I have ubuntu feisty for some months now
I recently changed my monitor (a CRT with VGA connection) and I bought a LG TFT 22" 1680x1050 resolution with dvi connection.

After that ubuntu displays strange colors as if i had 8bit color and not 24 bit.
I checked it even with nvidia configuration tool and i see no difference.

I have my pc dual boot with windows

With windows everything shows ok.

Anybody knows anything about it?


Dual Boot Windows XP + ubuntu Feisty
AMD Athlon XP 2600+
1 GB Ram ddr1
Nvidia GeForce 3 Ti200  64MB 1 vga + 1dvi

---

### Post by bibou91 on 2007-09-11
Perhaps your screen is not set correctly.

You may reconfigure it.

Do 
Ctrl+Alt+F1
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup * #it backups your xorg, so you can restore it later if you have problems*

sudo killall gdm* #kills your X because you will need to restart it*

sudo dpkg-reconfigure xserver-xorg #*go through the menu and configure, especially the screen part (simple detection works usually)*

sudo gdm


It may work then.

---

### Post by sotpar on 2007-09-13
I still have the same problem.

Seems like ubunty thinks that my graphic card does not sypport 24bit color depth.

Or it is a dvi thing.

Any idea how can i fix it?

The last thing I should do is reinstall ubuntu from scratch.

I tried run the live cd of xubuntu. I got normal colors but 1024x768 resolution ???

---

### Post by sotpar on 2007-09-20
I reinstalled Ubuntu and now everything works fine.
After i modified conf file

---

