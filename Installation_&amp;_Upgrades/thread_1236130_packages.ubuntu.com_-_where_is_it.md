---
title: "packages.ubuntu.com - where is it?"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by dcroxton on 2009-08-09
I have a new Asus Eee PC 1000HAB, with the unsupported Atheros wireless card.  I'm trying to download ndiswrapper packages onto another computer so I can install them on the Eee Pc, but packages.ubuntu.com just serves up blank pages -- no error, no content, nothing.  Is it just down for the moment, or is there something else going on here?  I don't know how else to install them on the computer, since it has no functioning networking, so I can't use apt-get.

Sincerely,
Derek

P.S. Gorgeous interface on UNR, I really love it and hope I'll be able to use it eventually.

---

### Post by Partyboi2 on 2009-08-10
Hi, it appears to be down at the moment, hopefully it will be back up soon.

Edit: If you have a Ubuntu cd put it in the cdrom drive and open a terminal (Applications>Accessories>Terminal) and[FONT=monospace]
[/FONT]```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndisgtk
```

---

### Post by dcroxton on 2009-08-13
Thanks, I should have been more patient.

---

