---
title: "[SOLVED] usb install on Aspire One"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by griz on 2008-12-11
I'm trying to load Hardy on an Aspire One, so need to do it by way of a usb key.  Have use the Create Usb Startup Disk on an Intrepid install on a pc, put usb in Aspire One, everything worked well until it came up with (initramfs).  Can get a list of built-in commands, but none of them seem to be able to help me.  I really need a quick fix for this please.

---

### Post by arubislander on 2008-12-11
Hi,

I'm afraid there is no quick fix. The Hardy implementation of a persistent usb boot (something to do with casper-rw and booting with the persist boot option) is broken. It has only been fixed in Intrepid. Even though you used Intreped to make the USB Startup-disk the image transfered on the USB is Hardy.

Have a look at: [www.pendrivelinux.com](www.pendrivelinux.com) and browse to their HOWTO of making a bootable Hardy. It has worked for me in the pass.

---

### Post by griz on 2008-12-18
Ok, loading Hardy was an absolute no go.  Wanted to go with that version because I found it easier to get my NextG wireless working, or so I thought.  Ended up loading Intrepid on my Acer One and everything worked, nearly out of the box.  Just had to load the GSM script, make some changes to it and then everything was fine.  The netbook is great because of the size, sits on my desk at work, where we have extremely limited access to the internet, without taking up too much space.

---

