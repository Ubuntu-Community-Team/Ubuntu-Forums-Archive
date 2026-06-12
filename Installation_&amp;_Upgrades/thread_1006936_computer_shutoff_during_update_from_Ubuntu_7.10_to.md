---
title: "computer shutoff during update from Ubuntu 7.10 to  8.04"
date: 2008-12-09
forum: Installation &amp; Upgrades
---

### Post by walkrun on 2008-12-09
help.. I,m a linux newbie and was trying to update my version of Ubuntu to 8.04 with synaptic package manager. During the update my laptop shutof and when I rebooted it failed to load Ubuntu. I get an organge screen. I am able to boot into a recover module and get to the command line, but can't get any further. Is there anyway to clean up, or remove, my upgrade so I can boot into Unbuntu? Also, I'm running a dual boot system with MS XP.

Thanks in advance for any help!

---

### Post by Partyboi2 on 2008-12-11
Boot into recovery mode and type
```
dpkg --configure -a
apt-get update
apt-get upgrade

```

---

### Post by walkrun on 2008-12-11
Thanks for the response. I tried that, but was unable to do dpkg --configure -a (I don't remember the exact error msg, but it was something like too many files were corrupted). Anyway, I went ahead and reinstalled both Windows and Linux. It's all good now. Time to learn Linux!

---

