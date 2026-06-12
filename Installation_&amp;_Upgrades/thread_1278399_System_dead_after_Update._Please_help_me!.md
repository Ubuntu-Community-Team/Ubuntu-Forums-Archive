---
title: "System dead after Update. Please help me!"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by stormfrog on 2009-09-29
Hi,

I have a laptop very dear to me and since I dont trust Linux system upgrades more than I can throw them I would never try an upgrade on my system.

HOWEVER, when I just UPDATED my Ubuntu 8.10 (being careful not to press the upgrade button on synaptic) I am first hit with error messages that some updates can not be applied. I redid the update and when Synaptic refreshes its screen after that update the Upgrade button is gone - as if the system decided to upgrade all by itself.

Updates reported numerous errors.

I reboot system and the GRUB shows this:

Ubuntu 8.10, kernel 2.6.27-14 generic
Ubuntu 8.10, kernel 2.6.27-14 generic (recover mode)
Ubuntu 8.10, kernel 2.6.27-11 generic
Ubuntu 8.10, kernel 2.6.27-11 generic (recover mode)
Ubuntu 8.10, kernel 2.6.27-9 generic
Ubuntu 8.10, kernel 2.6.27-9 generic (recover mode)
Ubuntu 8.10, kernel 2.6.27-7 generic
Ubuntu 8.10, kernel 2.6.27-7 generic (recover mode)
Memtest
Other OS:
Ms Win XP

2.6.27-14 
When I boot 2.6.27-14 I get a whole other graphical bootup screen (the bootup loader animation is much more slim and smaller). Boot up screens ususally only change with dist-upgrades from my experience leading me to believe this is really 9.04 booting(?).

It boots as far as trying to mount root. Then this happends:

"Gave up waiting for root device.
ALERT! /dev/disk/by-uuid/*(f00 numbers)* does not exist. Dropping to a shell!"

Booting in recovermode does nothing :(

Ive booted system from a livecd and tried to repair this mess. I mounted the root with chroot and tried to repair update. But when I do apt-get upgrade it says (200 something packages hold back).


2.6.27-9
If I try too boot this up everything seems to load just fine. BUT when X11/Gnome login starts graphics mode are all screwed up and I cannot do anything.


What should I do? I am trying to keep my calm but this computer has 2 years worth of work on it. Even if I have backup of my files, reinstalling the system takes a lot of time.

EDIT:

I downloaded 9.04 Live CD and booted into my system, chrooted and removed menu.lst and ran update-grub. Not grub Menu says "9.04". My UUIDS are correct, Ive checked UUID from blkid with fstab/menu.lst and they are all correct.

I also chrooted and did a apt-get dist-upgrade and apt-get install -f.

When booting Ive tried altering grub parameters and add rootdelay=130 - this makes boot take longer but still same problem. :(


Nothing helps so far. Im quite desperate! I would be extremely helpful for any advice!


[B]
Because of this thread I managed to get this shitty release of Ubuntu working.

[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)[/B]

---

