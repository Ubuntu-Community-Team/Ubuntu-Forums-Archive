---
title: "Monitor Refresh Rate Too High!!"
date: 2005-09-08
forum: Hardware &amp; Laptops
---

### Post by koolkat on 2005-09-08
My monitor says 47-63 Hz on the back. But currently at 800x600 its at 86 Hz. Is there a way to fix this?

---

### Post by tseliot on 2005-09-08
1) find the Horizontal and Vertical refresh supported by your monitor in your manual or on the internet (google)

2)Open either Terminal or Konsole and type:

sudo gedit /etc/X11/xorg.conf (if you use GNOME)

or

sudo kate /etc/X11/xorg.conf (if you use KDE)

scroll down the file and get to this section:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync [COLOR=Red]28-49[/COLOR]
VertRefresh [COLOR=Red]43-72[/COLOR]
EndSection

Set the numbers in red according to the refresh rate supported by your monitor.

Save and exit

3)Log out and press CTRL+ALT+Backspace

4)log in and enjoy.

---

### Post by duminas on 2005-09-08
Ooooooooooor you can
```
sudo ddcprobe | grep monitorrange
```to get the rates. First pair is HorizSync, second pair is VertRefresh. :P

You can also CTRL+ALT+Backspace and restart gdm ([font=Courier]sudo /etc/init.d/gdm restart[/font]), but again, it all comes down to method, and it all affects the same change, so. I say this as I've no experience with his step. ;_;

---

