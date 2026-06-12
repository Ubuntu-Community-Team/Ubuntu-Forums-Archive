---
title: "fresh install of 9.10 can't find any packages in the repositories"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Danbo19 on 2009-10-29
I just upgraded my laptop today, I did a fresh install and I am now trying to download some of my old packages and applications I had before and Ubuntu apparently can't find any. Here's what happened when I tried to install ubuntu-restricted-extras:

```
danny@danny-laptop:~$ sudo apt-get install ubuntu-restricted-extras 
[sudo] password for danny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

```The same is true for all other packages. Trying to install via synaptic is the same, no packages are listed and all I see are installed applications. Can anyone help? Thanks

---

### Post by Axos on 2009-10-29
This might be totally irrelevant (I know it says drivers) but give it a shot just in case...

Package list must be manually refreshed before installing drivers

The "Hardware Drivers" tool (Jockey) requires up to date package lists before it detects and advertises necessary driver packages. Immediately after a new installation, these package lists will not be present. Before running Jockey for the first time, update the package lists using System->Administration->Software->Update Manager (on Ubuntu) or "KPackageKit" (on Kubuntu). (462704)

---

### Post by Danbo19 on 2009-10-29
You sir, win... win something, I don't know. But it worked. Now I know to hit update manager before doing anything else on a clean install. Thanks!

---

