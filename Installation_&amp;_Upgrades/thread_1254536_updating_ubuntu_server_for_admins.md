---
title: "updating ubuntu server for admins"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by djxtc on 2009-08-31
i'm very new to ubuntu. i've been an experienced win admin for several years. 

i'm now trying to transition to ubuntu and i have lots to learn. 

how do you server admins update your servers? i will have a couple of ubuntu servers soon up and running so any tips or recommendations would be great.

---

### Post by slakkie on 2009-08-31
do-release-upgrade command.

I always do the following:

```

# Make sure everything is at latest and greatest
sudo aptitude update && sudo aptitude safe-upgrade

# You only need to do this the first time you will upgrade, from
# that moment on, it is installed and will be upgraded when you 
# upgrade your machine
sudo aptitude install update-manager-core 

# The actual upgrade
sudo do-release-upgrade

# reboot after upgrade, due to kernel updates

```

I also remove the preferences file, so packages can be upgraded. But you may or may not want to do this.

---

