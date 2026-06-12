---
title: "how to configure xorg.conf like a fresh install"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by nfolken on 2009-01-23
I installed ubuntu 8.10 on a computer with an embedded ati graphics chip. Everything looked good, so I updated and tried the fglrx driver, which didn't work. I uninstalled it, but now when i start, it still tells me "Ubuntu is running in low-graphics mode". Using the option presented to reconfigure doesn't fix anything, nor does "dpkg-reconfigure xserver-xorg" or "dpkg-reconfigure -phigh xserver-xorg". I don't have a backup xorg.conf, and the ones I do have are all very generic and sparce, only a dozen or so lines long.

Do I really have to manually create an xorg.conf file? the time in research alone makes reinstalling seem faster and easier. tweaking the file I can do, but Sax2  always did the majority of the work for me in opensuse. Is there anything like that for Ubuntu?

---

### Post by Pumalite on 2009-01-23
You could boot your Live CD, copy the xorg.conf file to a CD or external drive; backup yours and replace it with the new one.

---

### Post by nfolken on 2009-01-23
Interesting Idea... Let the liveCD create a new xorg.conf for my computer... I'll give it a try. 

Still though, surely there's a 'right way' about doing this

---

### Post by Pumalite on 2009-01-23
You wanted a new xorg.conf. That's it.

---

