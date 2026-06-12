---
title: "Update Manager error - UBUNTU 9.04"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by Wheel_nut on 2009-07-30
When Update Manager runs, I get the followin error. Please can anybody help:

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by dstew on 2009-07-31
Open a terminal window (Applications --> Accessories --> Terminal). Enter the command```
dpkg -l
```If this gives an error message, post it to the forum.

---

### Post by Wheel_nut on 2009-08-01
Thank you for your response Dstew.

I have just now managed to clear the error by opening a Terminal session and entering :

sudo apt-get update

That seemed to download the package list and cleared the error.

I hope this helps others who see this problem.

---

