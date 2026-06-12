---
title: "How to install the modules from http://dri.freedesktop.org/snapshots/"
date: 2005-08-14
forum: Hardware &amp; Laptops
---

### Post by mail2sona938 on 2005-08-14
I need it for installing i915 driver for my kubuntu linux

---

### Post by nad on 2005-08-14
These are all bzipped tarballs (what?). Compressed archives of the driver files. Probably source code.

As I use gnome, I am not certain if kubuntu will automatically recognize this, but, doubleclick the file and see if a utility pops up asking whether you wish to uncompress and/or untar.

I imagine that this will happen. Extract the files to a temporary directory and read any readme or install instructions to guide you through the procedure.

Post back with any questions and/or problems.

---

### Post by az on 2005-08-14
Install build-essential and linux-headers-(your kernel version)

Download the -common and the -i915 driver packages.  Uncompress them and they make a dripkg directory.  Go there and run theinstall script as sudo.

---

### Post by mail2sona938 on 2005-08-16
I tried, but when i type ./install , for any of the 3 - common, i815, i915, it says that i need the latest kernel modules to compile the driver....wat should i do?

---

### Post by kmi on 2005-08-17
[http://www.ubuntuforums.org/showthread.php?t=32043&highlight=dripkg](http://www.ubuntuforums.org/showthread.php?t=32043&highlight=dripkg)

hope this helps

---

