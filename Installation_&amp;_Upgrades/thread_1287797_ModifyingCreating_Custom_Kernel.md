---
title: "Modifying/Creating Custom Kernel"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by Pelsia on 2009-10-10
I've been searching through the forums and have found several good guides on how to update and install a new kernel, but none on how to *edit* one to include/exclude specific devices (I've got an intel 3945ABG wireless card that apparently needs to be activated in the kernel).

Until moving to Ubuntu I'd exclusively used FreeBSD (as a server, via command line only) where editing the kernel is done with vi and then compiled once the changes are made.  I admit that much of the ease of functionality with installation of modules with Ubuntu is done very well, though being used to creating makefiles and installing everything manually makes all this is a bit new to me.

Is there a way to edit the kernel file (obviously prior to compiling and installing) either graphically or through vi?  So far I've been coming up blank in this area in my forum searches and looking through various documentation sources.

---

### Post by Rich_Roast on 2009-10-10
Make menuconfig ? Sorry, might not have understood the post.

---

### Post by Pelsia on 2009-10-11
Sorry for the confusing post, I was able to fix my problem by editing one of the init.conf files to initialize the device at bootup rather than having to recompile a new kernel.  My laptop has the infamous intel 3945ABG wireless card and was a royal pain to get the thing working.

---

