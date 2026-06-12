---
title: "Problems with AWN, Emerald &amp; Python!"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by AbsentHarvest on 2009-05-28
Simply put...
I cannot run any of these things... there may be more... I don't know why they're not working... I've tried everything I don't know how to reinstall them.  I tried reinstalling, removal or upgrading.  I get this bloody error.

```
E: /var/cache/apt/archives/python-awn_0.3.2-0ubuntu2_i386.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/python-awn-extras_0.3.2.1-0ubuntu3_i386.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/python-awnlib_0.3.2.1-0ubuntu3_i386.deb: subprocess new pre-removal script returned error exit status 1
```

Then I get a pop up saying I suffered from a crash, and that I should report it.  Blah, blah, blah.

I don't know why emerald is having this problem... It looks more like AWN is the main cause of this.  None of them are working... Any solutions?

---

### Post by lemming465 on 2009-05-30
Does ```
sudo -i
aptitude clean
aptitude update
aptitude full-upgrade
```
help the situation any?  Sometimes cleaning out the APT cache clears up problems with corrupted package downloads.  

It can help to change the download server sometimes too, if a repository is having synchronization problems (Synaptic -> Settings -> Repositories; change the "Download from" drop down).

If neither of those quick & dirty brute-force simplistic solutions helps, you may be stuck delving into the intricacies of using dpkg directly.

---

