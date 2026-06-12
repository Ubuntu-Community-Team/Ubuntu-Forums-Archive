---
title: "Unable to upgrade"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by Carstairs on 2009-08-07
I have been off line for over a month trying to change ISP.
When I came back on I get a error message when trying to upgrade:

COULD NOT INITIALIZE THE PACKAGE INFORMATION

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I am quiet a new Linux user so please be gentle...........:(

---

### Post by Partyboi2 on 2009-08-08
Open a terminal (Applications>Accessories>Terminal) and remove the  file, then re-download it.
```
sudo rm /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
``````
sudo apt-get update
```

---

### Post by Carstairs on 2009-08-08
Many thanks for the help.
Now sorted, :D

---

