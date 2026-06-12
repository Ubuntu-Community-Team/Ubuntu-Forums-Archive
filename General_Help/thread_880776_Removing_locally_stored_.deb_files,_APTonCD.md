---
title: "Removing locally stored *.deb files, APTonCD"
date: 2008-08-05
forum: General Help
---

### Post by ragflan on 2008-08-05
Hi. When I partitioned my drive, I gave 10GB to mount point: **/** and 20GB for mount point: **/home** and 2GB for **swap**. I want to know something about APTonCD and Synaptic Package Manager. 

Correct me if I'm wrong, but if I install a package from Synaptic Package Manager the package is stored on my computer right? So, when I decide to uninstall and later reinstall, it won't re-download the package but it'll install the package which is stored locally. Correct?

I want to know if I can move the downloaded deb files to a portable hard disk and recover space from the **/** partition. If this is really stupid to assume, I apologise. 

I downloaded a lot of games from Synaptic and I was wondering if I can remove the locally stored debs. Like for example if I use the APTonCD program to backup all my downloaded packages, can I remove the locally stored ones? If I do, will the installed programs still run?

If I can remove the packages, how do I do that? If I can't, and I sounded really stupid, again I apologise. Thanks for the help, in advance.

---

### Post by Mgiacchetti on 2008-08-05
sudo apt-get clean  # this will clear the downloaded archive files
sudo apt-get autoclean # this will clear old archive files
sudo apt-get autoremove # this will clear all auto installed programs no longer needed.

sudo apt-get check #just to make sure your ok

---

### Post by ragflan on 2008-08-05
So, um... where are packages that are downloaded through Synaptic stored? If I want to move them to a backup drive that is. Also, the first command (**sudo apt-get clean**) removes all downloaded packages? Is that right? That should recover a significant amount of disk space, right?

---

### Post by Vivaldi Gloria on 2008-08-05
> **ragflan said:**
> So, um... where are packages that are downloaded through Synaptic stored? If I want to move them to a backup drive that is. Also, the first command (**sudo apt-get clean**) removes all downloaded packages? Is that right? That should recover a significant amount of disk space, right?

```
/var/cache/apt/archives
```

---

