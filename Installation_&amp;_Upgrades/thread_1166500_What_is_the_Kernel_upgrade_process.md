---
title: "What is the Kernel upgrade process?"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by VastOne on 2009-05-21
What is the Kernel upgrade process?  Not how to do it, but when does it happen and why?

I notice that I am at 2.6.28-11 and from this site: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) I see there is Kernel 2.6.29 and in its change log shows a tremendous amount of improvements and fixes.

Are Kernel changes left to the users or is there a revision level bridge that is met before it is mass released?

Thanks

---

### Post by snowpine on 2009-05-21
Ubuntu is a stable release distro; you will never get major changes to kernels, applications, or packages through the normal update process, only bug fixes and security patches. Major upgrades are lumped together every six months when a new "animal" is released. Jaunty will always use some sub-version of kernel 2.6.28.

This is not to say that installing a different kernel is impossible, just not officially supported nor recommended for beginners.

---

### Post by VastOne on 2009-05-21
Thanks

Not a beginner and quite comfortable at any kernel patch or update/grade, so if there is a plethora of fixes in 2.6.29 wouldn't it be wise to go there?  This is the real question of the Kernel process

So, where will Jaunty freeze at?  and is the new 30(RC6) for the next K release?

---

### Post by snowpine on 2009-05-21
Cool, I am always hesitant to send a beginner on a wild goose chase. ;)
All of the Ubuntu kernels are available here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I personally use 2.29. ;)

Good luck!

ps It is not definite yet, but Karmic Koala looks like probably 2.6.30.

---

### Post by VastOne on 2009-05-21
> **snowpine said:**
> Cool, I am always hesitant to send a beginner on a wild goose chase. ;)
All of the Ubuntu kernels are available here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I personally use 2.29. ;)

Good luck!

ps It is not definite yet, but Karmic Koala looks like probably 2.6.30.

Thank you snowpine...Appreciate all the kingdom of knowledge from you edge riders...

---

### Post by VastOne on 2009-05-22
> **snowpine said:**
> Cool, I am always hesitant to send a beginner on a wild goose chase. ;)
All of the Ubuntu kernels are available here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I personally use 2.29. ;)

Good luck!

ps It is not definite yet, but Karmic Koala looks like probably 2.6.30.

Snowpine:

Quick question

I am following these instructions

[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

but keep getting this

dpkg: dependency problems prevent configuration of linux-headers-2.6.29-02062903-generic:
 linux-headers-2.6.29-02062903-generic depends on linux-headers-2.6.29-02062903; however:
  Package linux-headers-2.6.29-02062903 is not installed.
dpkg: error processing linux-headers-2.6.29-02062903-generic (--install):
 dependency problems - leaving unconfigured

So I am left without headers

can you shed some light on this please?

---

