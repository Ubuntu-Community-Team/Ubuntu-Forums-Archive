---
title: "HP 932c - need help installing"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by djpenguin on 2006-10-18
I am attempting to install an HP 932c printer on a 6.06 Kubuntu system, and it is turning into an absolute nightmare.

After much searching, I finally figured out that I needed to use hp-toolkit to manage said printer (which was detected by hp-info), so I started it, and then saw a pop-up box instructing me to use the cups web interface to install the printer.  After clicking the button, I got to the cups web interface and attempted to add my new printer, but after I select the driver from a list and click the Add Printer button, a dialog box pops up requesting a username and password.  I've entered the user's info, and that did not work.  I tried entering root's info and password (yes, I know ubuntu does not have a root password by default, I set it), and still got nothing.

I attempted to run firefox as root so that I could hopefully use the cups web interface as root and bypass the password-requesting step, but it seems that another ubuntu "feature" is the total inability to run any X-dependent program as root (what the hell is up with that?) so that didn't go anywhere.

I've searched the forum and googled for answers, and I have come up with nothing, so I would really appreciate some help, even if it's just a hint on how to run X programs as root (like every other distro can.)

---

### Post by djpenguin on 2006-10-18
Never mind.  I finally got it installed using a part of the KDE Control Center and pointing it at the proper drivers located in /usr/share/ppd/hpijs/HP/

---

