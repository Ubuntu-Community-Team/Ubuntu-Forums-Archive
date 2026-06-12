---
title: "graphics card help needed"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by heiowge on 2008-04-15
Please help.

Main PC is dual booted XP and Ubuntu Gutsy.

Just put in a brand new nvidia geforce 6 PCI graphics card (6200, 256mb DDR2)

Managed to get XP to work, and my ubuntu login recognises the card insofar as it boots up with that displaying, but now all I get is a text based login, and a prompt.  no gui.

Before I try a reinstall, any ideas?

---

### Post by teaker1s on 2008-04-15
drivers may be required from nvidia, have you tried either vesa or nv driver to get gui
```
sudo dpkg-reconfigure xserver-xorg
```
if you can get a gui it would be easier to try "envy" nvidia installer than directly installing nvidia beta drivers


regards Dan

---

### Post by heiowge on 2008-04-15
it didn't recognise xorg

---

### Post by teaker1s on 2008-04-15
please check carefully as case sensitive

---

### Post by heiowge on 2008-04-19
Got it!  All installed now.

Ta!

---

### Post by teaker1s on 2008-04-20
:popcorn:

---

