---
title: "Grub dual boot Restricted video driver option"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by Teleskier on 2009-01-07
I am setting up Kubuntu to boot off a removable hard drive.  I would like to be able to select boot options from Grub with and without the restricted driver if possible (or safe video mode option for Kubuntu in Grub?).

Couple of reasons for wanting to do this:

1.  Last time I installed the ATI restricted drivers I could not see the screen and ended up  re-installing the OS.  I think I had enabled desktop effects.

2.  I would like to be able to boot from multiple computers using the removable drive, I don't know what will happen if the  other computers do not have a 3D graphics card installed.
Thanks.

---

### Post by sayakb on 2009-01-07
KDM is not affected by the restricted driver. So you can select it from the KDM sessions context menu instead.
If it anyhow happens, you can log into virtual terminal tty1 (Ctrl + Alt + F1) and remove your GPU drivers and reconfigure xorg from CLI and then login again.

---

