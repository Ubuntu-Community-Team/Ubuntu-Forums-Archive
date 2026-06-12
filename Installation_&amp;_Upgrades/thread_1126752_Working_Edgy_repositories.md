---
title: "Working Edgy repositories"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by zorbathut on 2009-04-15
I'm trying to install a single package on a truly ancient system that I do not want to upgrade if not necessary. It's running Edgy. Unfortunately, all the package listings seem to be gone - I get a ton of 404 errors doing "aptitude update", and visiting [http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/) shows only Dapper and Gutsy (and newer ones).

Is there any way I can find a still-running Edgy source? I'm obviously not expecting the latest and greatest software, just whatever Edgy still had when Feisty was released.

Alternatively, is there any way to update? I know in theory you can update one distro at a time, but since Feisty isn't listed in that source either, I'm not sure how effective that would be - unless I can just skip to Gutsy somehow, but that sounds dubious.

I'd really, really rather not reinstall the entire system, but I'd be willing to risk an incremental update through multiple years of distributions if that was the only choice :)

---

### Post by spiderbatdad on 2009-04-15
you can try to run ```
sudo update-manager -d
```Your update manager should start and offer you a distribution upgrade to accept. As you said it is not the best way to attempt multiple upgrades this way. Better to save the files you want on some media and install to 8.04 if you want an LTS release. Or clean install of jaunty. I recommend the latter.

---

### Post by Partyboi2 on 2009-04-15
You could try these repos
```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-backports main/debian-installer
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
```I agree with the previous post and that it would be better to backup your important stuff and do a clean install.

---

### Post by zorbathut on 2009-04-15
> **Partyboi2 said:**
> You could try these repos
```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-backports main/debian-installer
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
```

This worked perfectly. Thanks! If I ever need to update it majorly I'll definitely do the full reinstall, but I did not want to turn a ten-minute maintenance job into a multi-hour flatten and reinstall :)

---

