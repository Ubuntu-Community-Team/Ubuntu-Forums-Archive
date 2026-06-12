---
title: "External Resolution problem"
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by boom2k1 on 2006-08-01
I am using a laptop and it is connected to a 20" Samsung widescreen monitor.

It is very strange. When I start up my Ubuntu (I configured it so that only the external monitor is on.), the login screen recognizes my native resolution (1680x1050). I can tell because the font and cursor are small. However, after I log in and go into the main desktop, it resizes automatically to 1024 x 768 in GNOME.

Luckily, I can manually configure it so that it goes back to the 1680 x 1050.
It seems that XORG knows what resolution it is supposed to set at.

I also installed KDE. If I login to KDE, it stays in 1680x1050 and doesn't automatically resize to a smaller resolution, which is perfect.

Does anyone know how we can get rid of that annoying automatically resizing feature in GNOME?

Thanks!

---

### Post by wieman01 on 2006-08-01
Have you tried changing the resolution by using the Gnome "Screen Resolution" tool? You can find it in the menu. 

I am currently using KDE but I remember that Gnome had that.

---

### Post by boom2k1 on 2006-08-01
Perfect!

Thanks for your reply!~

What I did was System->Preferences->Screen Resolution
I would select the appropriate resolution and check the Options: Make default for this computer (computer name) only!

That does the job! :)

---

