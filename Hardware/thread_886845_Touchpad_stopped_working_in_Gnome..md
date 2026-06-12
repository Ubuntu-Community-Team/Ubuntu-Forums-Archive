---
title: "Touchpad stopped working in Gnome."
date: 2008-08-11
forum: Hardware
---

### Post by mirchichamu on 2008-08-11
I need help.I shall be thankful.

---

### Post by wolfen69 on 2008-08-11
go to synaptic package manager and search for gsynaptics. if it is installed, completely remove it. then do: ```
sudo apt-get clean
``` then ```
sudo apt-get autoremove
``` then re-install gsynaptics. reboot and see what happens.

---

