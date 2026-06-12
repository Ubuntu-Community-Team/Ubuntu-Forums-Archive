---
title: "Kubuntu: successful login return to login?"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by Bjerrum on 2009-02-08
I have Ubuntu running and within vbox I try to install Kubuntu. I get the GUI login and make successful login but instead of seeing the desktop I got the login screen again. Anny ideas how to fix this?

---

### Post by lemming465 on 2009-02-09
I'd describe that as an unsuccessful login, myself :-(

Personally, I do "sudo apt-get install kubuntu-desktop" on most of my ubuntu systems.  You can have multiple flavors installed simultaneously!  You can do it just for the applications, without switching the login (gdm vs kdm) or window managers.  Historically I've had better luck with gdm for user switching than kdm, but I haven't tried kdm recently, so it may have improved.

---

### Post by dabl on 2009-02-09
"Login loop" -- see:

[http://kubuntuforums.net/forums/index.php?topic=3097402.0](http://kubuntuforums.net/forums/index.php?topic=3097402.0)

---

### Post by lemming465 on 2009-02-09
Reverting to the login screen sounds kind of unsuccessful to me :-(  Check /var/log/messages and /var/log/Xorg.0.log in the vbox to see if there is anything useful there.  You can use Ctrl-Alt-F1 to switch to a text console.

Do you actually need the virtual machine?  I do *sudo apt-get install kubuntu-desktop* on most of my ubuntu boxes, because I like some of the KDE apps.  Your choice of whether to use gdm or kdm as the login manager; I've been using gdm because it was more stable doing user switching.  Also your choice of whether to Gnome or KDE desktops / window managers.

---

