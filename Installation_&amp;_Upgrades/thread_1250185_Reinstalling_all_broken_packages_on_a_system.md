---
title: "Reinstalling all broken packages on a system"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by lduperval on 2009-08-26
Hi,

I accidentally broke the apt database. The situation is this: the database thinks a lot of packages are installed, but in fact they are not. I would like to tell synaptic (or something else) to look at all the packages it thinks are installed, check to see if all the files for that package exist and if they don't, to mark the package as one to reinstall.

Is this possible?

Thanks,

L

---

### Post by dstew on 2009-08-26
You can try```
sudo apt-get --fix-broken
```

Repairing a broken apt system can be very difficult, depending on the problem. The hardest problems to fix result from a user deleting files directly, without using the dpkg system, or apt-get, or Synaptic. Sometimes you just have to re-install. See [this How-To]("http://ubuntuforums.org/showthread.php?t=186672"). The How-To is old, but the command-line techniques are still the same.

EDIT: [Here]("http://www.linux.com/archive/feature/48910") is a decent, more up-to-date How-To.

---

### Post by lduperval on 2009-08-26
Thanks for the info.

I ended up redoing an installation, but now, I notice that many, many, many(!) packages do not appear in Synaptic's list. For example: mysql, thunderbird, and apache to name but a few.

What can cause this? Is there a (quick) fix for it?

Thanks,

L

---

### Post by lduperval on 2009-08-26
OK, turns out the quick search doesn't work but a real search does. So let me see how I can get this to work.

Thanks again,

L

---

