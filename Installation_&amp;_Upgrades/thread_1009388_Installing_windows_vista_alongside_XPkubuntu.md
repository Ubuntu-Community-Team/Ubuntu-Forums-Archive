---
title: "Installing windows vista alongside XP/kubuntu"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by hydrogen18 on 2008-12-12
I've currently got XP installed on my laptop's primary partition, kubuntu lives in the extended partition. I want to install Windows Vista on the primary partition with XP(its ntfs of course). Kubuntu installed GRUB when I installed it, and automagically detected XP and set it up properly as a boot option. Is it possible to install Vista without overwriting the MBR and losing grub or will I somehow need to reload GRUB after installing Vista? Also, does Vista tend to nuke linux installs on the same disk drive when installing it?

---

### Post by Partyboi2 on 2008-12-12
Vista will rewrite to the mbr but you can boot a kubuntu live cd and follow [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351") to restore grub.

---

