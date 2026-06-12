---
title: "re-install ubuntu after cpu upgrade?"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Zadeet on 2009-06-29
Hi

A quick and maybe stupid question from an Ubuntu newbie:

I have an Ubuntu 8.04 server installation on an AMD Sempron with 3gig RAM, and my budget has allowed me to upgrade the CPU to a slightly newer cpu, AMD x2 7750 2.5GHz. My question is, can I upgrade the cpu without having to re-install the Ubuntu 8.04 server os, or do I have to re-install?

If I do need to re-install the os, is there a way of doing this without loosing precious settings and installed programs and my apt-cacher package cache?

Any help in this regard will be appreciated.

Thanks

Craig

---

### Post by WRDN on 2009-06-29
You should be able to upgrade the CPU without any troubles.

If you need to reinstall for whatever reason though, the best way to ensure your data is safe is to keep it on a seperate partition (/ on one, and /home on the other). This way, all system files will be seperated from personal files (/home), so you can reinstall without losing data/settings. Alternatively, just backup the data to a different medium e.g. CD

---

### Post by lotster on 2009-06-29
Zadeet, I recently upgraded from Athlon64 X2 to Phenom X4 on Ubuntu 8.10 and everything worked perfectly!  However, to be on the safe side, I recommend backing up your home directory, as well as all your downloaded programs and updates.  If you don't know how:

In Terminal; run

```
gksudo nautilus /var/cache/apt/archives
```

You will see all your downloaded packages (software and updates) here.  Copy them to some backup media (everything except the "Partial" directory and the "LOCK" file).

If you then need to re-install afterwards, then after installation just copy all those files back to the same directory and run "Update"; it will re-install everything without having to download all over again!

---

### Post by Arup on 2009-06-29
While on Intrepid, I upgraded from a dual core AMD to Phenom with a new motherboard. I have absolutely no issues.

---

### Post by Zadeet on 2009-06-29
Hi guys

THANK YOU ALL for the amazingly speedy replies!! Will order the new cpu tomorrow and get upgrading.

Once again thank you all!!

Cheers

---

