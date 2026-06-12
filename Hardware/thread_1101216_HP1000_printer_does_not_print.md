---
title: "HP1000 printer does not print"
date: 2009-03-20
forum: Hardware
---

### Post by raunhar on 2009-03-20
Ubuntu 8.10
Installed the printer. Ubuntu was able to detect the printer and install it without any problems.

But when I give the print command, it shows printing, but no printout. After a few seconds, the print icon (on system tray vanishes0.

Please suggest.

---

### Post by PRC09 on 2009-03-20
Hi,
  I used this link,hope this helps

[http://foo2hiperc.rkkda.com/](http://foo2hiperc.rkkda.com/)

---

### Post by raunhar on 2009-03-21
No success.

The properties showing are:
Device URL  hp:/usb/hp_LaserJet_1000?serial=0
make & Model  HP Laserjet 1000  Foomatic/foo...

When I click on test Page, it shows Processing, but after few seconds, goes to idle state without any print.

Please suggest.

---

### Post by PRC09 on 2009-03-23
Sorry for not replying sooner but you need to go to printer properties after the install from the link and change the device url to usb://HP/LaserJet%201000   Took forever to find that info on another forum....

Hope this works for you....

---

### Post by raunhar on 2009-03-24
Thanks a lot. It works now.
Just another query. Is benq 5000 USB scanner compatible with Ubuntu 8.10. If yes, how to configue/ make it work.

Thanks again

---

### Post by PRC09 on 2009-03-24
Glad it works,as for the Benq try this link,sorry I dont use a scanner so I have no experience with them at all.....

[http://www.sane-project.org/sane-mfgs.html#Z-BENQ](http://www.sane-project.org/sane-mfgs.html#Z-BENQ)

---

### Post by raunhar on 2009-04-22
The situation is that, I have to switch on the printer befpre starting UBUNTU, and have to keep the printer on the whole time. If I do not switch on the printer before hand, Ubuntu does not detects the printer on print command.

---

