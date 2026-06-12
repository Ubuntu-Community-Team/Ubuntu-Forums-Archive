---
title: "problem with windows partition"
date: 2008-07-25
forum: General Help
---

### Post by giuliopulina on 2008-07-25
Hi all,
in my notebook I have installed both WinXp and Ubuntu. 
Today, i made a mistake: 
- I mounted my windows partition on Ubuntu.
- I forgot to unmount it, hibernated Ubuntu and booted WinXP
- I hibernated WinXP and boot Ubuntu
- I made some changes (from Ubuntu) to WinXp filesystem

Result:
WinXP doesn't start anymore, i get only the flashing hyphen on the left-top corner of the screen. 
I tried to fix NTFS partition from Ubuntu using ntfsfix, but nothing changed :( However, the partition seems to be undamaged, and I can mount it from Ubuntu.
Any help???

Thanks in advance
Giulio

You can close the topic, now WinXp magically works again.

---

### Post by Eredeath on 2008-07-25
I'm fairly new to ubuntu but pretty well versed in XP, so i have a couple questions:
1. does unmounting the windows partition when in ubuntu and reboot produce any changes?
2. what changes in the file system did you make?

---

### Post by Daimoneze on 2008-07-25
You may want to consider booting a WinXP install CD and going into Recovery Console. From there you can run chkdsk /r. This will probably fix the NTFS partition.

---

