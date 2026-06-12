---
title: "Best way to make a 2nd partition for windows"
date: 2008-08-13
forum: General Help
---

### Post by gjr5017 on 2008-08-13
I want to make a partition that is like 3 GB or something so that I can install the zune software along with windows in that partition so taht I can sync my zune. I am having problems with VMware so I've decided to go this route. What would be the best way to do this so that I don't mess up anything with the boot loader.

---

### Post by finer recliner on 2008-08-13
1) you may need more than 3GB for windows

2) rule of thumb is to install windows first, because when you install windows, it will overwrite your boot loader

3) if you're not willing to start from scratch, install windows, and have a linux disc handy so you can boot from that and fix your boot loader to point back to GRUB

---

### Post by gjr5017 on 2008-08-13
> **finer recliner said:**
> 1) you may need more than 3GB for windows

2) rule of thumb is to install windows first, because when you install windows, it will overwrite your boot loader

3) if you're not willing to start from scratch, install windows, and have a linux disc handy so you can boot from that and fix your boot loader to point back to GRUB

I have a disc of stripped down version of windows. Its TinyXP. It's only like 100 some MB on the disc and the only piece of software I'm going to install is the Zune software. I don't really want to start from scratch because it took me a while to figure everything out being new to windows and I don't want to have to go back through and set everything up again. What would I have to do to fix the bootloader back to Grub?

---

### Post by finer recliner on 2008-08-13
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Howitzer777 on 2008-08-13
try virtualbox. paritions when installing windows don't go along that well. to my experiences anyway

---

