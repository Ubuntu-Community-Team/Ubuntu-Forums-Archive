---
title: "Requesting some help identifying a problem on my Toshiba Laptop."
date: 2010-08-14
forum: Hardware
---

### Post by Stev0 on 2010-08-14
I've recently purchased a Toshiba Satellite A665-S6070 and I installed Lucid 64 bit on it. At first glance everything seemed to be working fine. But then I ran into some problems. A quick search of the forums lead me to realize that perhaps Toshiba was not the wisest purchasing decision for ubuntu :)

The problem is that the laptop keeps entering a hard freeze randomly, and requiring me to actually hard power off the machine in order to regain functionality. Forums indicated I might need a BIOS update. Alas toshiba does not provide one for my model, I am assuming because it is a relatively new model. After looking through my BIOS it seems it came pre-installed with the updated version anyway. Phoenix SecureCore Tiano v 1.20?? I look through synaptic...toshet is already installed by default. Sounds seems to be working fine. Wireless, no problems. 

All in all I have no complaints except that it is freezing. Now I don't have toshutils or fnfxd installed. and i didnt do any of the acpi=off stuff, as those seem to be solutions to other hardware specific problems. I simply just put the CD in and let it go to town. I dont understand what is causing it to freeze as all the issues that pointed towards BIOS update in other threads are working fine on my machine. Any suggestions on how to go about solving this problem?

---

### Post by davidmohammed on 2010-08-14
what is your graphics card?

in a terminal type

lspci | grep VGA

---

### Post by Stev0 on 2010-08-14
I'm actually putting a fresh install on it right now so cant do the command. But its a nVidida Geforce 310M

---

### Post by davidmohammed on 2010-08-14
most nvidia freezes can be fixed by

a. adding nomodeset to your grub boot option
b. (sometime with a.) - using the recommended driver in Administration - Hardware drivers.

---

### Post by Stev0 on 2010-08-14
How can I be certain the freeze is caused by the graphics card?

---

### Post by davidmohammed on 2010-08-14
suggest have a look at your kernel log and/or x server log (administration - logs) and look for spurious stuff at around the time when you have to do a hard-reset.

certainly give the nomodeset option a go.  If it doesnt work for you, you can always remove it.  Likewise, if the recommended driver doesnt work for you, you can always deactivate it.

---

