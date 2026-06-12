---
title: "1GB Flash Drive Installation"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by Edozien on 2005-12-26
I have been using a minimal Ubuntu 5.04 server systems with a 1GB flash drive. I want to install Ubuntu 5.10 on a system with the same configuration. 

The guiding partitioning system creates (as with 5.04) ext3 partition hda1 of 950MB and swap partition hda5 of 74MB. The install fails trying to format hda5 with the error message:

"The attempt to mount a file system with type swap in IDE1 master, partition #5 (hda5) at none failed  ... "

Does anyone know how I can get around this problem?

---

### Post by Edozien on 2005-12-26
UPDATE
-------

I repeated the installation allocating the entire 1.0GB as ext3 hda1 file system. The installation failed formatting the ext3 file system.

I tried the installation allocating 960MB as ext3 hda1 file system and the rest as free space. This seems to work!

Can anyone explain this?

---

