---
title: "How to remove nouveau nvidia drivers from Meerket?"
date: 2010-09-27
forum: Hardware
---

### Post by ene_dene on 2010-09-27
I don't know why are these drivers default, they have no use at all. New users will run from ubuntu because of it. 
Removing them seems impossible on my laptop. Installing the real nvidia drivers doesn't remove them so I went to synaptic manager and tried to remove everything neuveau in package name, I did except for libdrm-nouveau1 which threatens to remove all ubuntu packages, then I blacklisted:
blacklist amd76x_edac
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
in /etc/modprobe.d/blacklist.conf
They still load, I tried to get into a single user mode, but they still load and sudo rmmod -f nouveau says that driver is in use and I can't do nothing...
Is there a way to remove these useless drivers from 10.10?

---

### Post by goldenbrown on 2010-09-27
> **ene_dene said:**
> I don't know why are these drivers default, they have no use at all. New users will run from ubuntu because of it. 
Removing them seems impossible on my laptop. Installing the real nvidia drivers doesn't remove them so I went to synaptic manager and tried to remove everything neuveau in package name, I did except for libdrm-nouveau1 which threatens to remove all ubuntu packages, then I blacklisted:
blacklist amd76x_edac
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
in /etc/modprobe.d/blacklist.conf
They still load, I tried to get into a single user mode, but they still load and sudo rmmod -f nouveau says that driver is in use and I can't do nothing...
Is there a way to remove these useless drivers from 10.10?

Press: Ctrl Alt F2

Type: sudo apt-get stop gdm

Type: sudo apt-get remove nvidia*

That will remove all nvidia drivers

Type:sudo apt-get install nvidia_185*

Type :sudo apt-get start gdm 



That will install only 185 drivers

---

### Post by ene_dene on 2010-09-27
> **goldenbrown said:**
> Press: Ctrl Alt F2

Type: sudo apt-get stop gdm

Type: sudo apt-get remove nvidia*

That will remove all nvidia drivers

Type:sudo apt-get install nvidia_185*

Type :sudo apt-get start gdm 



That will install only 185 drivers
Nope, I did all that, nouveau drivers just don't go away, they always get loaded in kernel, because of that I always have the maximum resolution in console.
I want to install the newest drivers from nvidia site and they say they are not compatible with nouveau that I should blacklist the nouveau, but it doesn't help. I've installed nvidia drivers a million times before, I like to have the newest version, but I can't move this one... I'll try the fresh install/removal of the broken drivers, and see where will it take me, I did it on my desktop.

---

### Post by ene_dene on 2010-09-27
I had better luck after reinstallation.

---

