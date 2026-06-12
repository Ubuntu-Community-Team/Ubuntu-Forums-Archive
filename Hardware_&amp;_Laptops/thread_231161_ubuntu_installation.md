---
title: "ubuntu installation"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by Kmujo on 2006-08-07
ok, i had to connect my laptop 2.5" hdd to a desktop pc in order to install ubuntu 6.06 lts due to no cd/dvd or fdd hardware & setting up a dhcp for a pxe installation was just a bit overwhelming. anyways i managed to get it installed and everything, but i knew that it'll come at a cost of repairing something. so xorg.conf probed the hardware setup from the desktop computer, so i was wondering is there anyway to probe the current hardware and update the xorg.conf? i've tried installing the ati video drivers, but no luck.

it's a Dell Latitude L400 btw

---

### Post by fourchannel on 2006-08-07
on your laptop try running ```
sudo dpkg-reconfigure xserver-xorg
``` and see if that is what you need. What kind of errors do you get when installing the ati drivers, if you could post the output here it would speed up trying to find the problem.

---

