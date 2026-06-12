---
title: "Installer can't mount CDROM"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by Consul on 2009-05-15
I'm trying to go from Ubuntu 9.04 64-bit to UbuntuStudio 9.04 32-bit (so I can use Supercollider), and the installer for UbuntuStudio has thrown the strangest error, and I can't get around it.

After the language and keyboard selection, it pops up a window saying the CDROM can't be mounted, which is odd considering that my DVD drive has been working perfectly otherwise, including booting to an installation DVD-ROM. It asks if I want to try mounting again, and if I keep hitting enter on the Yes option, it just keeps coming back saying it can't mount. I kept hitting Yes a bunch of times, and was able to catch a glimpse of the command it was issuing:

mount /dev/sr0

I've never heard of a device called sr0 before this. Of course, the line following that (which again can be briefly seen), just says that the device can't be found.

Any suggestions? Thanks!

---

