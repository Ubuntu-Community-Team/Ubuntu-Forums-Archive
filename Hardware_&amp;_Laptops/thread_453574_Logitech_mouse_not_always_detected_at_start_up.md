---
title: "Logitech mouse not always detected at start up"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by thayerw on 2007-05-24
This minor annoyance is finally getting to me... My Logitech MX 518 is not always detected after a cold or soft boot.  I have to unplug it from the USB port and plug it in again before Kubuntu correctly detects it.  This started happening while using Ubuntu 6.10 Edgy with GNOME, so it does not appear to be KDE/GNOME related.

My specs:

Dell Inspiron 6400
2GB Memory
100GB HD
X1400 ATI Gfx

I have also tried using a different USB port, but that had no effect on the problem.  It works fine under Windows too.

Any suggestions?  Could it just be a module getting loaded a little too late in the boot sequence?

Thanks in advance.

---

### Post by aidanr on 2007-05-24
see my post [here]("http://ubuntuforums.org/showpost.php?p=2529007&postcount=15")

(sudo aptitude install lomoco if you haven't already or just leave that part out)
the rmmod usbhid && modprobe usbhid parts are what you need, if you automatically login then you can stick it in your regular startup items, otherwise somewhere like .xinitrc

that's just a workaround btw, not a solution

---

### Post by thayerw on 2007-05-24
Thanks for the tip, I'll give it a shot... anything is better than reaching behind my laptop after each reboot.

---

