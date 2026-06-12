---
title: "Missing ttys with ATI proprietary driver in Ubuntu MATE 15.04"
date: 2015-07-12
forum: Hardware
---

### Post by cogset on 2015-07-12
After installing the ATI proprietary driver (fglrx and fglrx-amdcccle packages) from the official repository in Ubuntu MATE 15.04, I've discovered that I've lost all six my virtual consoles: I now only have six blank screens except the fact that (luckily) Ctrl+Alt+F7  still gets me back to the graphical environment.

  I'm reasonably sure this has happened because of the proprietary fglrx driver installation, so is there any way around this?  I really hope I'm not stuck between either doing without the virtual consoles (you never know when you may need them...) or the ATI proprietary driver (the Gallium driver isn't bad at all, but still won't allow me to set the display brightness -which is very annoying- and use stuff such as Compiz effects) .
  _____________________________________________________________________________________________

 _EDIT_: I'm now 100% sure it is indeed the flgrx driver, because I've removed it and the six consoles are back. 

  Now what? I can't imagine I have to choose between using the proprietary driver or having the consoles, as a matter of fact both in Lucid and Precise I had this proprietary driver installed and zero issues with the consoles. 
 The only difference that I can think of is that the driver was manually installed there, whereas in 15.04 I took the easy route and simply installed it from the repo.  So, is there any workaround that you folks are aware of ?

---

### Post by cogset on 2015-07-16
It has recently been reported as a bug here: [When using fglrx module, the virtual consoles are blank and useless ]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/1470862"), unfortunately I see it's confirmed but  still unassigned.                      

I wonder if it would be worth a try to install  manually the latest ATI driver (15.20) from the AMD site.

---

