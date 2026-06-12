---
title: "Mounting DVD/CD disks only once per boot."
date: 2008-11-08
forum: General Help
---

### Post by gimfred on 2008-11-08
I´ve had this curious problem that I can only mount an optical disk once per boot. I definitely had the problem with 8.04, think I had the problem with 7.10 and 7.04.

I´m currently running Kubuntu 8.10 with a side-grade to Xubuntu. (KDE4 is not loading the desktop -- don´t worry about that now) I have nvidia 177 drivers installed.

I can´t manually mount anything unless the drive was empty on boot. If I have mounted a disk and eject it no other disk will mount.

Between 8.04 and 8.10 I replaced the drive but nothing changed. The drive does automatically retrieve the tray after being ejected (anywhere from 3 - 360 seconds.

Drive is /dev/scd0

---

### Post by gimfred on 2008-11-29
none of the updates have changed this problem. I'm not sure what else I can do???

---

### Post by editrix on 2008-11-30
Just found this in another thread, which may or may not work, but ...

> in /etc/fstab one specifies how drivers should be mounted at boot time. There is one line there for the cdrom thatt probably looks something like this:

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

try changing the option "user" to "users"

The Original Poster had a different problem from yours. The complete thread is at: [http://ubuntuforums.org/showthread.php?t=984944&page=2](http://ubuntuforums.org/showthread.php?t=984944&page=2)

---

### Post by gimfred on 2008-12-08
Thank you

---

### Post by gimfred on 2008-12-08
actually that does not work.  :S but thanks anyway. It appears to be hardware because every user has the same problem. Being root doesn't help. I've changed everything but the motherboard; I'm thinking it must be the motherboard. 

What is a recent AMD64 M/b with ide ports that every feature works with linux?

---

### Post by gimfred on 2008-12-27
Now weirdly it seems to have corrected itself... bar some written disks...

---

