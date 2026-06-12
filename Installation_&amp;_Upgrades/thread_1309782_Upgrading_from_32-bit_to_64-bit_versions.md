---
title: "Upgrading from 32-bit to 64-bit versions"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by TheRedDragon on 2009-11-01
I've updated from 9.04 to 9.10 (32-bit) successfully, and have no problems to resolve.  I wonder, however, if it is possible to migrate from 9.10, 32-bit, to 9.10, 64-bit without starting with a freshly formatted drive, and in the process, losing all the modifications I'd made and the software loaded under the 32-bit version.  :confused:

---

### Post by SuperSonic4 on 2009-11-01
Nope, you have to reinstall although if you have a separate /home you can use that although some settings may be off

---

### Post by IgnorantGuru on 2009-11-01
Make a copy of your /home folder to another drive (partition) or USB stick, eg:
```
sudo cp -a /home /mybackuplocation
```

If /home contains your music, video, and other large files, you may want to back those up separately, perhaps to DVD-Rs.  Other than those user files, /home should not be very large.  In fact you could also tar /home and burn it to CDR.

When you install the 64 bit version, use the same username.

After your fresh install with 64 bit, when you get to the login screen, press Ctrl-Alt-F1 to get a shell.  Login to the shell, then copy your /home folder back...

```
sudo rm -r /home
sudo cp -a /mybackuplocation/home /home
```

Press Ctrl-Alt-F7, then login.  Most of your settings should be restored.  You just need to add the additional programs back in using apt-get or another package manager.

---

