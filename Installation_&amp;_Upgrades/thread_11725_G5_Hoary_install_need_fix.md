---
title: "G5 Hoary install need fix"
date: 2005-01-18
forum: Installation &amp; Upgrades
---

### Post by Brian McConnell on 2005-01-18
So, I got Hoary onto my dual 1.8ghz G5. I can't boot into it, though. It looks like I need to edit the yaboot.conf file. I see some say I need to use the Gentoo live PPC64 cd to do that. Could someone please provide a newbie a step-by-step on that? When I cd to /etc or /boot in the gentoo live, it takes me to, presumably the gentoo system. 
What can I do to use Ubuntu? I had it sweet with my g4 emac and Ubuntu. But I need some help for the g5.

---

### Post by humberto on 2005-01-20
[QUOTE=Brian McConnell]So, I got Hoary onto my dual 1.8ghz G5. I can't boot into it, though. It looks like I need to edit the yaboot.conf file. I see some say I need to use the Gentoo live PPC64 cd to do that. Could someone please provide a newbie a step-by-step on that? When I cd to /etc or /boot in the gentoo live, it takes me to, presumably the gentoo system. 
What can I do to use Ubuntu? I had it sweet with my g4 emac and Ubuntu. But I need some help for the g5.[/QUOTE]

Actually, try doing another install, but choose custom-power4 as the target, then select a power4 kernel from the list of available images (I think linux-power4). The install-power4 boot option installs the powerpc kernel instead, which cannot boot on the G5. I did an expert-custom-power4 install, but ended up without X, emacs, or other nice stuff.

On Hoary Array 2, I did not need to change the yaboot.conf.

---

### Post by Brian McConnell on 2005-01-20
so instead of install-power4, I should use custom-power4 and then select a g5 image. I think I can do that. I shall post back here with my findings. Also, I'm installing Ubuntu to a USB drive. Can I put the bootlader on the same disk or does it have to be installed to sda/hda instead of say ,sdb?

---

### Post by humberto on 2005-01-21
[QUOTE=Brian McConnell]so instead of install-power4, I should use custom-power4 and then select a g5 image. I think I can do that. I shall post back here with my findings. Also, I'm installing Ubuntu to a USB drive. Can I put the bootlader on the same disk or does it have to be installed to sda/hda instead of say ,sdb?[/QUOTE]

Array 3, released yesterday, should fix the kernel selection problem. I'm downloading it now.
 
:D 

We tried to install linux to an external firewire drive, but can't figure out how to tell openfirmware how to boot from it. You'll probably be better off putting the bootloader on an internal drive (you only need a very small partition).

---

### Post by Brian McConnell on 2005-01-21
[QUOTE=humberto]Array 3, released yesterday, should fix the kernel selection problem. I'm downloading it now.
 
:D 

We tried to install linux to an external firewire drive, but can't figure out how to tell openfirmware how to boot from it. You'll probably be better off putting the bootloader on an internal drive (you only need a very small partition).[/QUOTE]


well, I still had bootloader issues after installing to USB drive. I installed YellowDog to the internal afterwards, it boots fine. I think if I can just update my yaboot.conf in YellowDog, I might be able to just add an entry for Ubuntu. Not sure, but am gonsta try ;)

---

### Post by joey on 2005-06-03
see [this thread](http://ubuntuforums.org/showthread.php?t=38864) for more details

---

