---
title: "Considering HP tx2500z purchase..."
date: 2009-01-04
forum: Hardware
---

### Post by Doctor_Gonzo on 2009-01-04
So I can't stop looking at this tablet...But before I take the plunge on it I'm wondering just how compatible this beast is with Ubuntu. I'm assuming it involves a little tweaking, but I'd like to hear how other users are coming along with their tablets...

---

### Post by Favux on 2009-01-06
Hi Doctor_Gonzo,

Lots of folks are using TX2500's with Ubuntu.  If you install Intrepid it will take a little work to install the linuxwacom drivers and configure your xorg.conf.  But no biggie.

The main issue is that the proprietary ATI video drivers don't support rotation of your screen.  So to go to tablet mode you have to use Xorg's "radeon" driver.  But ATI just released a bunch of driver stuff to open source.  So drivers will probably improve rapidly.

---

