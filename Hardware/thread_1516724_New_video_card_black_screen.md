---
title: "New video card: black screen"
date: 2010-06-24
forum: Hardware
---

### Post by Call on 2010-06-24
Hi to all.

Recently my old graphic card (geforce 8600 gts) died, leaving me with  modern art boot screens full of red squares, green lines or white dots.  Ubuntu was replaced by little green waves.

So I have replaced the card with an asus eah5570. I have a dual boot  with vista and under windows it works without problems (not too many at  least).

When I boot into ubuntu (lucid) I get instead a black screen and the  monitor switches to idle. Ubuntu works (there is the login sound) but I  can't see anything.
I can't see anything even if i switch to terminal session (Ctrl+Alt+F1).

Even the lucid live cd does not work. The 9.04 live cd works but the  graphic is not perfect.

What can I do? Any suggestion?
[This thread]("http://ubuntuforums.org/showthread.php?t=1463961") seems to apply, but I do not really  understand. Moreover I can't really experiment around not seeing a  thing.

Any help will be much appreciate,
Marco      

 EDIT: I have it working connencting the monitor with the VGA insted of the DVI. Any idea on how the get the DVI working?

---

### Post by dino99 on 2010-06-24
you can boot with video=vesa on the boot line

then remove the xorg.conf: sudo rm -f /etc/X11/xorg.cong

reboot and check driver activation (system admin hardware driver)

latest xserver releases works well, install this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

