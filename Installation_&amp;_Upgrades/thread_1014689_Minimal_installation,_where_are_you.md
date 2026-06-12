---
title: "Minimal installation, where are you?"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Gargamella on 2008-12-18
Since ubuntu 7.10, I can't find anymore the command line installation the wiki suggests for minimal installation on old HW computers.

Mine is 400 Mhz intel celeron cpu, 64 mb ram, so it is not that easy with a live cd and it gets stuck during the installation process or it is simply too slow after, so I would like to have a clean command line installation (ubuntu-based distro) and to install there after Xorg, openbox and all the lightweight programs i need, but how?

No command line installation in 8.04 and 8.10 ubuntu variants
No way to select packages

Somebody told me about Minimal Cd image... what's inside there?
Maybe that is the right way.


Somebody to help this man?

Thanks 

Andrea

---

### Post by overdrank on 2008-12-18
> **Gargamella said:**
> Since ubuntu 7.10, I can't find anymore the command line installation the wiki suggests for minimal installation on old HW computers.

Mine is 400 Mhz intel celeron cpu, 64 mb ram, so it is not that easy with a live cd and it gets stuck during the installation process or it is simply too slow after, so I would like to have a clean command line installation (ubuntu-based distro) and to install there after Xorg, openbox and all the lightweight programs i need, but how?

No command line installation in 8.04 and 8.10 ubuntu variants
No way to select packages

Somebody told me about Minimal Cd image... what's inside there?
Maybe that is the right way.


Somebody to help this man?

Thanks 

Andrea

Hi and you can find the mini.iso here
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by urukrama on 2008-12-18
For a command line install, you'll need to use the alternate install CD. You can download it [here]("https://help.ubuntu.com/community/Installation/").

The minimal CD downloads only the packages you need. The computer on which you will install Ubuntu will need a good internet connection, in other words.

---

### Post by Bachstelze on 2008-12-18
> **urukrama said:**
> For a command line install, you'll need to use the alternate install CD. You can download it [here]("https://help.ubuntu.com/community/Installation/").

I believe since Hardy, the Alternate CD cannot install command-line systems anymore (or at least I didn't find out how to do it), one has to use the Server or Minimal CD.

---

### Post by kerry_s on 2008-12-18
with those specs you should try a faster distro such as arch or pure debian.
denian lenny net installer:
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

uncheck desktop
log in as root
apt-get install xorg openbox ...

---

### Post by urukrama on 2008-12-18
> **HymnToLife said:**
> I believe since Hardy, the Alternate CD cannot install command-line systems anymore (or at least I didn't find out how to do it), one has to use the Server or Minimal CD.

I install a command-line Ubuntu system with the Alternate CD for Hardy. You have to press F4 now to see the option (or F5, I forget). I haven't tried Intrepid yet, but I assume that hasn't changed.

The server install CD adds to a command-line install some server applications, which most normal users won't need.

---

