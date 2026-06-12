---
title: "USB drive not detected during boot from USB"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by xpacker on 2009-09-21
I'm trying to install Eeebuntu Base 3.0 on my Asus 900ha netbook via USB. However, when I press Esc as instructed (there is never an Asus logo), my computer still goes to Windows. I tried pressing F2 during another boot and changing the boot-from device order (and saving it), but it still runs straight to Windows.
 
I made the bootable USB on my Jaunty virtual machine (create bootable usb). For some reason, I had to partition/format it first using gparted.

---

### Post by bumanie on 2009-09-21
I am not sure which function key you need to press to get into your bios settings, but it will flash up on the screen, (very quickly) at some point at the end of the POST cycle. It should say something like <del> to enter setup or F12 to enter boot menu or something of that nature. You will then need to set the bios to boot from usb if it has that option - not all bios' allow that, but a fairly new netbook should.

---

### Post by raymondh on 2009-09-21
after post, try either

F2
Del
Ctr + alt + Esc

---

### Post by xpacker on 2009-09-23
Thanks for your quick responses.  I found my problem: the USB drive was listed under the HDDs in the BIOS.  I had assumed it was the Removable Device.  A bit frustrating...

---

