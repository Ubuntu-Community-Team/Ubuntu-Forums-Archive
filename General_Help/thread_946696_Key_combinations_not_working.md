---
title: "Key combinations not working"
date: 2008-10-13
forum: General Help
---

### Post by eleifsp on 2008-10-13
I recently fixed my graphics driver and installed XFCE and KDE4.1 on my normal Ubuntu distro.  For some reason, the key combinations that normally work aren't working.  Here's a list:

Ctrl+Alt+Bkspce
Ctrl+Alt+F#
Ctrl+Z

Also, logging out has ceased to function correctly (I get a blank screen with a cursor).  Anyone know what files/packages might be broken?

EDIT:
BTW, I'm running Linux kernel 2.6.24-21-generic.  The 2.6.27 kernel has some problems on my computer.

---

### Post by adaptr on 2008-10-13
XFCE *and* KDE ? and which startup script is it executing ?
Which DM is it using ? (XFCE uses GDM or XDM ; KDE comes with KDM).
Read your X session log to see what happens; also check your X variables inside an xterm.
Is keyboard support properly set for your X session ?

EDIT: Blank screen on logout ? hmm sounds like a busted xinit procedure.

---

### Post by eleifsp on 2008-10-13
Well, Gnome, XFCE, and KDE, with KDM as the default.  I'm using KeyTouch to enable the use of certain keys on my keyboard (I have an HP Special Edition Laptop with extra media touchpad icons).  

Where would I find the Xinit script/What is it's name (so that I can locate it)?

Oh, if it's any help (probably not), when I wake my computer up from sleep/suspend, it has some blue static lines go across the screen (kinda like an old TV that didn't have any signal, but with blue instead of white or gray, and without the noise).

---

