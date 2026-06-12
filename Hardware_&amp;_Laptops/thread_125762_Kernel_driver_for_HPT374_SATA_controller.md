---
title: "Kernel driver for HPT374 SATA controller"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by The Belgain on 2006-02-04
Well I'm in the process of getting my Highpoit 1540 SATA controller working under Ubuntu, and am just about there.

One thing that's bugging me: in order to get the card working, it's necessary to recompile the kernel making sure that the driver for this card is NOT compiled into the kernel.  After doing that it's a matter of compiling the driver from Highpoint, and loading it as a module.

Now what I don't understand is: if the driver included in the kernel for this device doesn't work (the system hangs at boot when loading the driver if there are any drives connected), then why is it included?  Am I missing something here?  If it weren't for this non-working driver, it would have been pretty simple to get this hardware working, whereas instead it's needed a kernel recompile.

---

### Post by dik666 on 2006-10-05
Hi Belgian.  Did you ever get an answer to your post?  I am doing the same thing with a HighPoint 1640 on Ubuntu 6.06.  I really don't want to open a can of worms by doing kernel compiles so I am considering switching to a different distro.

Does anyone know if Ubuntu 6.10 will have the HPT366 driver built into the kernel?

Thanks for the help,
  dik666

---

