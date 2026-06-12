---
title: "Can't find common applications with apt-get"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by chudak on 2009-05-01
I just wiped my harddrive and did a fresh install of Jaunty. I'm also running Jaunty on another laptop that I upgraded for Intrepid.

I'm trying to reinstall some common applications that I have on my other machine and had on this one before the reinstall but I can't seem to find them in the repos:

grsync
fslint
ghex
vpnc

Example:

> 
chudak@chudak-laptop:~$ sudo apt-get install ghex
[sudo] password for chudak: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ghex


WTF?!

I have all the normal Canonical repositories enabled and these applications are 'supposedly' in the jaunty repositories based on:

[http://packages.ubuntu.com/jaunty/ghex](http://packages.ubuntu.com/jaunty/ghex)
[http://packages.ubuntu.com/jaunty/vpnc](http://packages.ubuntu.com/jaunty/vpnc)

etc

Any ideas?

---

### Post by zvacet on 2009-05-01
All packages are from** universe** repository.Enable universe and multiverse in **system>admin>software sources** and you will be able to install that packages.

---

### Post by tom56 on 2009-05-01
If that doesn't solve it try running
```
sudo apt-get update
```

---

### Post by zvacet on 2009-05-01
> If that doesn't solve it try running
Code:
sudo apt-get update

That can not help if he doesn´t add repos where packages are.

---

### Post by Peasantoid on 2009-05-01
> **zvacet said:**
> That can not help if he doesn´t add repos where packages are.
He's saying that *after* the OP adds the repos, *then* do "sudo apt-get update" if it doesn't work.

---

### Post by tom56 on 2009-05-02
Actually, since multiverse is enabled by default, I thought that maybe it's in their sources.list but their mirror had been down last time they did an apt-get update.

---

### Post by chudak on 2009-05-03
> **Peasantoid said:**
> He's saying that *after* the OP adds the repos, *then* do "sudo apt-get update" if it doesn't work.

I already had the repos enabled.

However, after I did an update, the package list got updated and the applications were available. Apparently they weren't in the package list included with the installer.

Thanks for the helps folks!!

---

