---
title: "Re-installing 9.0.4 with XP Partition"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by PaulHeywood on 2009-05-08
Hi there - I want to re-install 9.0.4 on my Samsung NC10, it currently duals boot with XP, has a shared partition and a Samsung 'recovery' partition, when I boot (USB Stick) the partition editor gives this :

Vista Loader, /dev/sda1/ 6G ntfs
XP Home, /dev/sda2 34.8G ntfs
Ubuntu /dev/sda5, 47.1G ext3
[Share I think] /dev/sda7 30G fat32
Swap /dev/sda6 3G
Samsung Recovery (I think) /dev/sda3 32G ntfs

so I just want to pop the 9.04 over the top of the old Ubuntu, if I delete the ubuntu partion it gives an error "No root file system is defined"

any ideas ?

---

### Post by Partyboi2 on 2009-05-08
At the partitioning stage choose "manual' and set the mount point for sda5 (if this is the root partition) as / and tick the box to format. This will format and reinstall ubuntu to sda5 so make sure you have backed up your important stuff.

---

### Post by PaulHeywood on 2009-05-08
Thanks PartyBoi - Looks like I have to hit edit, select it as a ext3 system then the installer lets me check the "format" box and select "/" as the Mount Point... sound right ?

---

### Post by Partyboi2 on 2009-05-08
Yeah that sounds right :)

---

