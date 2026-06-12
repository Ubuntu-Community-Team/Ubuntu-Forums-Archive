---
title: "both USB and PS2 mouse at the same time"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by f_s on 2007-08-13
Hi all

running ubuntu 7.0.4

both a USB mouse and PS2 trackball are connected.  The mouse worked for some time, then suddenly stopped working and then only the PS2 trackball did work. I guess after a restart the mouse will be ok again.

Question: beyond the graphical config dialogs, where are the mice config files? how can one find out what's actually wrong when e.g. one the two stop working?

cheerz

f

---

### Post by ddrichardson on 2007-08-13
Input devices are defined in /etc/X11/xorg.conf under Devices. I have a PS/2 device (touchpad) and a USB mouse that I use from time to time and both work fine - at the same time infact.

---

### Post by eentonig on 2007-08-13
I have a PS2 mouse and a USB Wacom tablet. Both work all the time.

---

### Post by f_s on 2007-08-14
yeah! thanx! checked it out yesterday evening and the USB mouse worked perfectly well; but I did not touch the trackball, lest the mouse would "dissappear"

thanx!

---

### Post by f_s on 2007-08-19
hm...bugger me...the USB mouse sometimes simply stops working when the PS2 one still goes on....there any way to "re-initialize" the USB ports?

cheerz

F

---

