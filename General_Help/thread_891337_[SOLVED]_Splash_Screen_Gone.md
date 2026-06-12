---
title: "[SOLVED] Splash Screen Gone"
date: 2008-08-16
forum: General Help
---

### Post by gjr5017 on 2008-08-16
I attempted to install a new splash screen for Ubuntu but instead of getting a splash screen I just completely lost my other one and I have no idea about how to get it back. Now when I turn on my computer it goes through the Grub Bootloader and when my computer is loading, instead of seeing an image with a loading bar I just see a black screen with white lettering saying what the computer is doing....How do I get it back?

---

### Post by angry_johnnie on 2008-08-16
There is an app called startupmanager, which has a nice graphical way to manage usplash themes, grub timeout, default os, and so on.

You'll find it in synaptic (system > administration > synaptic).

or by typing

```
sudo apt-get install startupmanager
```

in a terminal.

Or, maybe it's just disabled in grub's configuration file (menu.lst).
Post the output of

```
grep kernel /boot/grub/menu.lst
```

Somewhere in the "kernel" lines, there should be something like 'ro quiet splash.' Maybe that's just missing.

---

### Post by Uchiha_madara on 2008-08-16
Easy ... Easy My friend :


Look for these Steps I tried them Yesterday :

1 - Connect to the internet.
2- you must to install the Startup Manager :

> sudo apt-get install startupmanager

3- after that : 
Click on System menu - then from Administration choose Startup Manager
or from terminal write :
> sudo startupmanager

then click the button "Manage the boot splash" - it is the last button in the Screen i think" to add or remove 

when you click on it you well find List of splash screens "the Default one and the other's you've installed .


If you have any problem or if it works with you reply

:KS:KS:KS

sorry because bad English >>>>>

:guitar::guitar::guitar:

---

