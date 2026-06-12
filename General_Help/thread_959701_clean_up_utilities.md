---
title: "clean up utilities"
date: 2008-10-26
forum: General Help
---

### Post by thirdeye420 on 2008-10-26
hey everyone,

just wondering if there is some sort of program/utility out there that could be used to clean up my ubuntu system of old files that are probably useless now.  can anyone recommend a good one?

---

### Post by dracayr on 2008-10-26
at the command line, these commands clean up your unused program files and cache:

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

dracayr

---

### Post by LowSky on 2008-10-26
sudo apt-get autoremove
 it will get rid of packages that are not required anymore

---

### Post by OrangeCrate on 2008-10-26
On Ubuntu 8.10, there is a new utility called "System Cleaner". It'll already be installed, or you'll have to find it in Synaptic (I've been on Intrepid since an Alpha, so I don't know how it'll roll out.) I've used it, and it works great.

Here's something about it:

[https://wiki.ubuntu.com/CleanupCruft](https://wiki.ubuntu.com/CleanupCruft)

And, like the other posters above, I also use:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
```

---

