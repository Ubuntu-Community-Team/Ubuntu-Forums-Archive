---
title: "Will IBM Hard drive active protection work for the M4?"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by mapage on 2006-06-21
I have a Toshiba M4 Tablet PC.  It has a button that will change the orientation of the screen depending on which end of the tablet is 'up'.  So far, it doesn't work under Ubuntu, but it looks like this software from IBM might do the trick.  

Hey 23meg, do you think this will work?  Have you played with it?

Here is an excerpt from the website.  (Link below text)

Driver and user-space test application for IBM's Hard Drive Active
Protection System (hdaps)

The driver exports a device node, /dev/hdaps, which may be read and a bunch of sysfs files.

The driver also exports an input class device that allows the laptop to
act as a pinball machine-esque mouse.  See the sysfs file mousedev to
enable this feature.

[http://hdaps.sourceforge.net/index.php?page=1](http://hdaps.sourceforge.net/index.php?page=1)

---

### Post by 23meg on 2006-06-22
I don't think this will work with Toshiba since it seems to have been written specifically for the system used in IBM laptops. There's no way of knowing for certain though, since it's totally undocumented. Still worth going to the project's IRC channel and asking about support for Toshiba's HD protection support though; maybe they know of a similar project.

---

