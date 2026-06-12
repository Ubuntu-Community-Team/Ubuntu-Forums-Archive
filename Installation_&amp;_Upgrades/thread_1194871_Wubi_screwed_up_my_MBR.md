---
title: "Wubi screwed up my MBR?"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by revan86 on 2009-06-23
I recently installed Kubuntu next to XP (same partition), but it turned out to be buggy(it crashed after logout) so I decided to uninstall wubi from Windows and try an older version of Ubuntu instead. AFter rebooting, the GRUB menu still appeared with the options Windows and Kubuntu, even though I've uninstalled it minutes ago. I've tried the fixmbr command, but it didn't work. Do I have to reformat my Windows partition?:confused:

---

### Post by presence1960 on 2009-06-23
edit your boot.ini file by removing the reference to wubi/Ubuntu. see this thread : [http://ubuntuforums.org/showthread.php?p=7501325#post7501325](http://ubuntuforums.org/showthread.php?p=7501325#post7501325)

---

### Post by Mark Phelps on 2009-06-23
For future references ... I don't believe that Wubi touches the MBR at all; instead, what it does is modify the boot.ini file to add a reference to itself.

So, as presence has said, if you remove the reference from the boot.ini file, you should be OK now.

---

### Post by revan86 on 2009-06-23
Thanks guys, I removed the redundant entry from the .INI file, everything is fine and dandy!

---

