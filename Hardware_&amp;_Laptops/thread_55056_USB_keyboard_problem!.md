---
title: "USB keyboard problem!"
date: 2005-08-07
forum: Hardware &amp; Laptops
---

### Post by fastb on 2005-08-07
I've had ps2 keyboard but now i've bought a new usb keyboard(genius luxemate scroll). It doesn't work! It works in bios but when kubuntu boots up it doesnt work. How can I get it to work?

Thanks

---

### Post by Subfix on 2005-08-07
I have the same problem with a Logitech USB mouse in Ubuntu... anyone know anything about this?

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 open a konsole/terminal and write

sudo dpkg-reconfigure xserver-xorg

follow the on screen instructions ...

---

### Post by Jaymoid on 2005-08-10
[QUOTE=Gezzer]open a konsole/terminal and write

sudo dpkg-reconfigure xserver-xorg

follow the on screen instructions ...[/QUOTE]
 I have a similar problem, I have a USB keyboard (Saitek Eclipse), but it will not work in grub so I can't select the OS I want to boot into. It does however work in Ubuntu and windows, when they load up.

Any ideas? I've had a look in the bios and there doesn't appear to be a setting to switch the keyboard to usb.

I have the keyboard plugged directly into a usb slot that is attached to the motherboard (rather than one that is on a host card or a hub). My motherboard is an asus a7v8x.

Thanks in advance.

---

