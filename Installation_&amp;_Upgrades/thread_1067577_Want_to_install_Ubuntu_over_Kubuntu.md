---
title: "Want to install Ubuntu over Kubuntu"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Azure.Rise on 2009-02-12
I'm dual booting Windows 7 and Kubuntu. My previous install was Vista and Ubuntu and while I was doing that Ubuntu ran pretty great. Now that I've got Kubuntu it's really buggy so I want to install Ubuntu again. Can I just install Ubuntu over my Kubuntu partition without affecting my windows install to have a Windows 7 Ubuntu install?

---

### Post by x33a on 2009-02-12
you can install ubuntu on the kubuntu partition without any problem.

another thing is that you can install gnome, and make it your default manager. that way you will have ubuntu and kubuntu with the same install.

---

### Post by Vico Vicario on 2009-02-12
Ubuntu and Kubuntu only differ on the desktop. Just type 'sudo apt-get install ubuntu-desktop' from kubuntu to install ubuntu specific files including gnome. You can then reboot and select gnome session and later remove Kubuntu with 'sudo apt-get remove kubuntu-desktop'.

---

### Post by Azure.Rise on 2009-02-12
Yeah I installed over it. Overwrote "/". It wasn't just the desktop environment, it was really buggy. Things are fine now in Ubuntu.

---

