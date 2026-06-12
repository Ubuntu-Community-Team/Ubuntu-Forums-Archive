---
title: "Are hibernate works in kubuntu 5.10 ?"
date: 2005-11-05
forum: General Help
---

### Post by htower on 2005-11-05
Hello, I have installed kubuntu breezy and found that hibernate package don't work :( 

```
# hibernate

Your kernel does not have any recent Software Suspend 2 support compiled in.
Please follow the HOWTO linked from http://softwaresuspend.berlios.de/ for
instructions on how to compile Software Suspend into your kernel.
hibernate: Aborting.

```

And a don't know - it's my problem or it's normal for this release ? This commant was tested on kernels 2.6.12-9-386 and 2.6.12-9-686 from ubuntu's repositary.

P.S. sorry for my bad english

---

### Post by Copter on 2005-11-06
hi!

i works just fine here on default (2.6.12-9-686) kernel. check in system settings -> laptops and power -> laptop's battery -> acpi config is hibernate enabled.

copter :]

---

### Post by sciurus on 2005-11-09
Is it possible to make suspend/standy/hibernate appear in KDE's log out menu? Right now it only says, end session, turn off computer, restart computer, and cancel, even though those other options are enabled in ystem settings.

---

### Post by Copter on 2005-11-10
hmm.. dunno. i have a KLaptop icon in the tray that i can right click for these options to pop up. its the only place i have seen these _buttons_ on my system.

---

