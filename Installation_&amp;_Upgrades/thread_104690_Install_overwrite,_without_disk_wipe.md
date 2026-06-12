---
title: "Install overwrite, without disk wipe"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by ninstints on 2005-12-16
I have an Red Hat installation on one partition and Windows XP on another, I want to install over the Red Hat installation and NOT wipe out the existing Windows XP and Grub Loader install.
Has anyone any experience with this?

---

### Post by NotJustANewbie on 2005-12-17
In the Ubuntu install, install Ubuntu on your Red Hat partition, making sure that the Windows partition isn't up for formatting (go to manual editing of partition table). Then when Ubuntu is installed with a new GRUB (probably), edit the new GRUB to the spec that you want. It's not too difficult really.

---

