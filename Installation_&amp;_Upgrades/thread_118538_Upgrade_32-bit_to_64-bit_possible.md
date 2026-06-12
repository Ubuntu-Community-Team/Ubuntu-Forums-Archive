---
title: "Upgrade 32-bit to 64-bit possible?"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by l:x on 2006-01-17
I've a SN25P with an AMD 3200+ Venice 64-bit CPU.
I've installed Ubuntu (rather then Debian) because it supports all my hardware at once.

The only problem with the 64-bit version is that I can't run all software because these are 32-bit. I installed a 32-bit chroot, but that doesn't seems to work for every application.

Anyways > Is it possible to install a 32-bit system and upgrade it later to a 64-bit system? 
So I can start using my workstation without any special tricks to get everything working. In the meantime I'll install a 64-bit on my laptop and try the solutions on that one.

Another question: can you upgrade from Debian to Ubuntu without a reinstall?

---

### Post by Haegin on 2006-10-13
Kind of. In reality, no - go and do a reinstall to change architectures. In theory you can clear out some of the apt stuff, remove practically everything and use debootstrap to install a 64bit system manually after you have installed a 64 bit kernel then you can go from there. Though this is almost guarenteed to break your system.
If, like me, you are curious about the install process you can always do it manually from a live cd by formatting the volumes and using debootstrap to set up a minimal system then install the rest using apt. I'm still looking in to it as a learning experience.

---

