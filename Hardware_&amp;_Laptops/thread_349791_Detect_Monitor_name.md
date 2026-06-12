---
title: "Detect Monitor name"
date: 2007-01-30
forum: Hardware &amp; Laptops
---

### Post by cgrado on 2007-01-30
I was configuring the xorg.conf file and i couldn't remember the name of my monitor, so i left it as generic monitor.  I am now stuck with 1024x768 resolution. How do i find the name of the monitor is should use and what should i change in the xorg.conf file to make it work?

I have the NEC MultiSync LCD 1970GX

---

### Post by teaker1s on 2007-01-30
find out vertical and horizontal sync spec for your monitor and then
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]
for monitor choose expert mode and you can tell xserver your spec

---

