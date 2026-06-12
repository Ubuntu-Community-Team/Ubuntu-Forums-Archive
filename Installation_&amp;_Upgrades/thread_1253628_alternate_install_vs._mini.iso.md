---
title: "alternate install vs. mini.iso"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by entropy1 on 2009-08-30
If I want to do a command line install, what is the difference between using the alternate install .iso or the mini.iso to set up the command line installer and run the commands that I need?

---

### Post by snowpine on 2009-08-30
You can use either disk. The mini.iso is tiny and needs to download everything from the web. The alternate disc contains everything in a full Ubuntu install, so you have the choice of a full or command line only install (it's one of the Fn keys, forget which one).

---

### Post by entropy1 on 2009-08-30
One difference is that the alternate install .iso can be used to make a usb startup disk, but the mini.iso cannot.

---

### Post by SuperSonic4 on 2009-08-30
The mini.iso has very little on it. It's better if you want a base CLI install and you want few programs on it or a WM instead of a DE.

The alternate install will install a specific flavour of ubuntu from the CD, it's like the Live CD without the graphics.

---

### Post by earthpigg on 2009-08-30
in addition to what others have said,

the mini.iso's install will come with all the most up-to-date software. just make sure you 'sudo apt-get update && sudo apt-get upgrade' prior to installing ubuntu-update or any other meta package.

the alternate install will still be looking at '5 million updates required' at first boot.

---

