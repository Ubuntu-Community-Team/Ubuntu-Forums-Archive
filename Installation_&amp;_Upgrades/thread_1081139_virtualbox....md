---
title: "virtualbox..."
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by nikhil_bafna on 2009-02-26
i installed win xp thro virtual box, but facing couple of problems...
the windows is not coming full screen,, even when i use the option "full screen" there are two black stipes at the edges...
its not detecting my pen-drive
how to access this partition from ubuntu??

---

### Post by barnex on 2009-02-26
Make sure you have the virtual machine additions installed. If this does not fix the fullscreen issue, try playing around with the screen resolution in windows.
As far as I know, Virtualbox-OSE does not support usb passthrough, so you won't see any usb devices. You can access the files on ubuntu from within windows via a "network disk", you can find out how to do this in the documentation. This should also allow to see your pendrive, assuming you have access to it under ubuntu.

---

