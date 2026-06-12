---
title: "Touchpad problem"
date: 2008-09-17
forum: Hardware
---

### Post by UV-Ray on 2008-09-17
Out of the box synaptics touchpad on my Acer Aspire 1690 notebook works perfect. Yesterday it stops working completely - no left or right button, no movements, no scrolling.

When I noticed this, I played in game Enigma - hope it does not related ;)

In xorg.conf I tried to move "CorePointer" to synaptics section,  removed "SendCoreEvents", also I enabled SHMConfig and used "synclient -m 1" to test touchpad - no changes on the screen while clicking or moving.

Kernel boot options from [this thread]("http://ubuntuforums.org/showthread.php?t=844968&highlight=touchpad") does not help too.

USB mouse works fine.

1) Can I check is it hardware or software problem? Something like cat /proc/touchpad
2) Where I can look for diagnostic messages?
3) Can I remove it and run hardware detection again? How?

Thank You.

---

