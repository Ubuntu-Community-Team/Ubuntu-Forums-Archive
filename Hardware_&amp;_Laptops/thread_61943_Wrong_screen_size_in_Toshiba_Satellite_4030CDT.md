---
title: "Wrong screen size in Toshiba Satellite 4030CDT"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by last1 on 2005-09-02
Hi
I'm having this problem with getting the installer to take up the entire screen on my laptop, and since I know from previous experience trying other distros on this thing that it'll stay that way after installing, I figure I need some help. I've tried using the vga=771 boot parameter, and that made the size a little bigger, but still not the entire screen. 

Anybody got a suggestion for me to try?

---

### Post by last1 on 2005-09-02
Nevermind, I got it, I needed to use vga=791

---

### Post by last1 on 2005-09-02
Aw, man...I got it to go fullscreen when it was installing using that boot parameter, but now that it's finished installing it's back to the tiny screen again! WTF??!!
Can somebody please help me out here?

---

### Post by az on 2005-09-02
On my 460CDT, I had to pick 15-bit color depth since It does not have enough vram for more than 480x600 at 24-bit.

sudo init 1
dpkg-reconfigure xserver-xorg
init 2

---

### Post by last1 on 2005-09-02
:grin:  \\:D/ 
THANK YOU!!!!!!

---

### Post by adageapad on 2008-06-07
I have a Sattellite 4030 cdt and had this problem.
I searched web and found a driver for this.
The driver is Trident Cyber 9525 dvd agp w98.
I hope this helps all suffering with this annoying small screen problem.

---

### Post by gobetno on 2008-06-09
> **adageapad said:**
> I have a Sattellite 4030 cdt and had this problem.
I searched web and found a driver for this.
The driver is Trident Cyber 9525 dvd agp w98.
I hope this helps all suffering with this annoying small screen problem.

How do you manage to install Win98 driver in Linux?:confused:

---

