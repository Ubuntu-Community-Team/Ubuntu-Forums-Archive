---
title: "fedora"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by ubunewtu on 2009-10-27
ok heres the deal i have a computer with red hat fedora core two? on it im trying to install ubuntu 9.04 with a cd i make it to where it starts to do the install and crashes at 5% and brings me to the live session screen. i want to use the entire hd for the install cuz its a small one only 7g ive done many installs before but im pulling my hair out on this one how can i solve this

---

### Post by jjcv on 2009-10-27
I suggest you open a terminal from the Applications menu.

The do a "fdisk /dev/hd0"  replace hdo with whatever your hard disk is.

The delete the current partition.

Save the configuration  "w"

Then reboot the system from the cdromm again  (you need to do a restart for the HD changes to take effect).

This time installation should go fine.

---

