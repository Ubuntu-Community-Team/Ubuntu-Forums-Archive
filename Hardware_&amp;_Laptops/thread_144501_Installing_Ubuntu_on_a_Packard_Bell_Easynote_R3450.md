---
title: "Installing Ubuntu on a Packard Bell Easynote R3450"
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by superstaas on 2006-03-14
(I post this hoping that it may benefit someone, in the same way I benefited from the Ubuntu fora during my own installation process.)

Installing Ubuntu "Breezy" on a Packard Bell Easynote R3450 laptop is a nightmare: the graphics card, and more importantly, the network card do not function well. (Alternatively, it is a great way of spending a few working days learning about Linux internals, if you believe in persistent failure as a means for character building.)

Luckily, the "Flight 5" alpha version of Ubuntu "Dapper" *does* work on this machine!

If you'd like to try this, instead of waiting for the stable version of "Dapper" to arrive, here is a short description of what to do:

First, it may be wise to perform a BIOS update (via windows XP) using "enr3_bios_101.exe" (you can find it in the section "Easynote R3 Series" on [http://support.packardbell.com/nl/download/)](http://support.packardbell.com/nl/download/)).

Then download and burn the i386 install CD from [http://cdimage.ubuntu.com/releases/dapper/flight-5/](http://cdimage.ubuntu.com/releases/dapper/flight-5/)

(Do not use the AMD64 version if you value functioning Flash and Realplayer when browsing the web. Also, the AMD64 version messes up the colors of the Ubuntu boot screen.)

On booting the i386 install CD, press [ESC] and [ENTER] to leave the graphical menu. Type as boot options: "install vga=771 noapic nolapic", then press enter.

During the install process, answer "no" to the "system time is UTC?" query if you have a dual boot setup with windows XP.

When the maximum X server resolution is asked, check the "1280x800" option.

When booting up the new system after successful installation, you'll probably notice that connecting to the internet fails.

A workaround for this is typing "sudo dhclient eth0" in a terminal (to manually activate DHCP discovery). After this your internet connection should function properly.

That's it!

---

### Post by chrisxp on 2007-10-04
bleh, hijacked your topic, sorry..

delete pls?

---

### Post by Lady Jane on 2008-05-04
I just surfed over your thread about the Packard Bell Easynote. Thanks for placing it. 
Now I have the Easynote MX51-B-062. And I´d like to get rid of Windows. 
Do you maybe know anything about problems with this type of Easynote? Most important things for me are wireless and sound (obviously).
In here there are a AMD Turion 64 and the graphics are from Nvidia (geforce go 6100).

---

