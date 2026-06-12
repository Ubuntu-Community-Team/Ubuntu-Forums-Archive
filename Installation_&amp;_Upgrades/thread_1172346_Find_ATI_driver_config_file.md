---
title: "Find ATI driver config file"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by artsci2 on 2009-05-28
Where is the configuration file for ATI driver? I've got two 1680x1050 monitors on an AIW 2006 video card and apparently need the proprietary driver to use both. However Catalyst Control Center sees one of the screens as a 1680x1050 and the other as a lower res monitor. It also insists on making the "Big Desktop" resoulution to be 3200x1200 (should be 3360x1050). I have had this system working before and even tried re-install of Ubuntu 8.10 with continued trouble (problem started when I installed 9.04).


I found that "amdcccle" is the command for Catalyst control center but a search for files with that name gave no results.

---

### Post by markbuntu on 2009-05-28
Did you try detect monitors in CCC?

Anyway you cannot edit the config file by hand. You need to use the command aticonfig or edit /etc/X11/xorg.conf

aticonfig --help

for a list of options.

---

### Post by Mark Phelps on 2009-05-29
Don't use the ATI driver anymore, but from some old notes, I found a reference to /etc/ati/amdpcsdb.  Fglrx loads this file to get its options.

Problem is that it apparently can only be updated using aticonfig.

You can type "aticonfig --help" to get a full list of options.

---

