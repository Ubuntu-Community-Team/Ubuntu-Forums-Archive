---
title: "[SOLVED] How to restore pre-8.10 CD/DVD automount behavior?"
date: 2008-11-22
forum: General Help
---

### Post by cogadh on 2008-11-22
Before upgrading to 8.10, any time a CD/DVD was inserted, it was automounted to a generic directory, usually /media/cdrom0 (or /media/cdrom1, depending on the drive used). With 8.10, it seems to be dynamically creating a mount point based on the CD/DVDs label, such as /media/KotOR_1 (as happened when I put in my KotOR install disk). This is causing problems for me with some custom scripts I have created, as well as with the proper use of Wine. Is there any way to restore the automount behavior I am used to from previous Ubuntu versions?

---

### Post by mc4man on 2008-11-22
Mounting to /media/volume_name is usually a sign that the fstab entry(s) are incorrect.
If you did an upgrade you may also wish to ck. here for duplicate drive entries

```
cat /etc/udev/rules.d/70-persistent-cd.rules

```

---

### Post by cogadh on 2008-11-22
Well, there are no fstab entries at all for my cdrom drives (only hard drives) and this was on a clean installation (wubi style). Since this was just a testing machine, I did a complete uninstall/reinstall using each variant of 8.10 (Ubuntu, Kubuntu, Xubuntu) and they all exibit the same automount behavior. Just for giggles, I also did an install of Kubuntu 8.04 (also wubi style) and found that it actually had the proper fstab entries for both of my cdrom drives and a floppy drive, which was also missing from the 8.10 installs (I completely forgot I had one). I copied the fstab entries from the 8.04 install into the 8.10 install and it now works correctly (or at least it works the way I want it to). Thanks for the help!

---

