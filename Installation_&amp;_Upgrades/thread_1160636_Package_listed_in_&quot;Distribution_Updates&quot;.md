---
title: "Package listed in &quot;Distribution Updates&quot; won't upgrade"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by daniel_summers on 2009-05-15
I installed Xubuntu 8.10 from disc, and upgraded to 9.04 via the network.  Since I upgraded, there's been a package that's listed in Update Manager every time I run it under the heading "Distribution Updates."  It cannot be selected, and if I run "apt-get upgrade" at the command line, it says that it's been held back.

I set this as "all variants" because I encountered it with straight Ubuntu in an earlier release.  What causes this, and what, if anything, should I do (or do I need to do anything at all)?

If you need specifics - on my current installation, the package is "banshee"; on the previous one, it was "xine".


Thanks...

---

### Post by zvacet on 2009-05-16
```
sudo apt-get dist-upgrade
```

---

### Post by daniel_summers on 2009-05-16
```
summersd@johnson:~$ sudo apt-get dist-upgrade
[sudo] password for summersd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  banshee
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Isn't "dist-upgrade" what you do to actually move to a new version (i.e. 8.10 to 9.04)?

---

### Post by kpkeerthi on 2009-05-16
> **daniel_summers said:**
> ```
summersd@johnson:~$ sudo apt-get dist-upgrade
[sudo] password for summersd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  banshee
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Isn't "dist-upgrade" what you do to actually move to a new version (i.e. 8.10 to 9.04)?
No. See **man apt-get** command.

---

### Post by daniel_summers on 2009-05-16
Well, that certainly explains how I hosed up my headless server trying to upgrade to 9.04...  No big problem, though, as I'd been meaning to install Ubuntu Server on it, with LVM to bridge the two disks.  I could have sworn that I read something about that, but upon rereading the man page, that's not what I originally read.

So, by the fact that it's holding banshee back, does that mean that there are dependencies that it requires that would break other programs?  If so, is there a command to list the conflicts?

---

### Post by daniel_summers on 2009-05-26
Anyone?  How can I tell what dependencies are not being met, or are conflicting?

---

