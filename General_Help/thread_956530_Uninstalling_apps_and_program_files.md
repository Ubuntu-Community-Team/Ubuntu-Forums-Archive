---
title: "Uninstalling apps and program files"
date: 2008-10-23
forum: General Help
---

### Post by And6ate9 on 2008-10-23
What's the best way to uninstall programs and and user config files from a .deb package?

I want something that will erase it all

is it aptitude purge?

---

### Post by Peter09 on 2008-10-23
If you installed it through synaptic or the package manager then just go there, find the apt and tick the box again with the remove option.

System->Administration->Synaptic

---

### Post by sethvath on 2008-10-23
Remove - removes the deb and all its known dependencies
Purge - all of Remove + configuration files

In terminal: sudo apt-get remove --purge filename

In Synpatic: locate the file and right click "completely remove" and apply

---

