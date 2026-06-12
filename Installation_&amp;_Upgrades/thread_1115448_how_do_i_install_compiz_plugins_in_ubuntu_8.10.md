---
title: "how do i install compiz plugins in ubuntu 8.10?"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by shresthanator on 2009-04-03
I am trying to get the atlantis aquatic plugin for compiz. I have been following the instructions on here: [http://wiki.compiz-fusion.org/Install/PluginsFromGit](http://wiki.compiz-fusion.org/Install/PluginsFromGit)

The part that I need help with is when it says : can be done by entering the newly created directory and running make, then make install. Do not use sudo...". How do I "enter the created directory", what does that mean? When I just type make into the terminal it says no target specified and no makefile found. I'm very new to ubuntu, so I need as much help as I can get- could someone give me step-by-step directions as to what to do? Thanks a lot.

---

### Post by Lunx on 2009-04-03
> **shresthanator said:**
> I am trying to get the atlantis aquatic plugin for compiz. I have been following the instructions on here: [http://wiki.compiz-fusion.org/Install/PluginsFromGit](http://wiki.compiz-fusion.org/Install/PluginsFromGit)


You can get it from synaptic, just look for the unsupported plugins or from the terminal 

```
sudo apt-get install compiz-fusion-plugins-unsupported
```

I've got it working on this box :)

---

