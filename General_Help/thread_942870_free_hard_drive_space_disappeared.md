---
title: "free hard drive space disappeared?"
date: 2008-10-09
forum: General Help
---

### Post by timstone on 2008-10-09
I was trying to install an mp3 player a few minutes ago and it told me I don't have enough space to install it.  I only have a few apps downloaded and 1 movie.  Ubuntu is installed on a 30gb drive, it says I'm using about 12.7GB according to disk space analyzer.

Whats going on?

i ran rkhunter just for the hell of it and found this at the end of the file

```

[16:45:07] Performing filesystem checks
[16:45:07] Info: Starting test name 'filesystem'
[16:45:07] Info: SCAN_MODE_DEV set to 'THOROUGH'
[16:45:24]   Checking /dev for suspicious file types         [ Warning ]
[16:45:24] Warning: Suspicious files found in /dev:
[16:45:24]          /dev/shm/pulse-shm-3926908586: data
[16:45:24]   Checking for hidden files and directories       [ Warning ]
[16:45:24] Warning: Hidden directory found: /etc/.java
[16:45:24] Warning: Hidden directory found: /dev/.static
[16:45:24] Warning: Hidden directory found: /dev/.udev
[16:45:24] Warning: Hidden directory found: /dev/.initramfs

```

---

### Post by timstone on 2008-10-10
bump

---

### Post by timstone on 2008-10-11
bumpity bump!  can anyone help me?

---

### Post by timstone on 2008-10-12
bump again

---

### Post by earthpigg on 2008-10-12
trash can is empty, right?

---

### Post by timstone on 2008-10-12
not empty, there are 2 items in there that i cant remove for some reason, but even with those they dont equal like 15GB

---

### Post by PsychedelicReaction on 2008-10-12
try Applications->Accessories->Disk Usage Analyzer and see how the space is allocated

---

### Post by drs305 on 2008-10-12
You probably have some 'root' trash that a user can't delete without assuming administrative privileges. Open nautilus with:
```
gksudo nautilus
``` 
to find and delete trash.

In Hardy:
Normal trash: ~/.local/share/Trash
Root trash: /root/.local/share/Trash

Refer to the link in my signature to find out where all the free space may have gone and ways to regain it.

---

### Post by timstone on 2008-10-12
ok ill try everything suggested...im on XP right now so ill try later and report back

---

