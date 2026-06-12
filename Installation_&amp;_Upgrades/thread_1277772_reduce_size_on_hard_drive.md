---
title: "reduce size on hard drive"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by newbemac on 2009-09-28
I have ubuntu 9.04 installed on my asus 701, all works fine and i am happy with it....but I am running out of space, the solid state HD is 4 gig and Ubuntu is taking 3.5.  I gave no music, photos, files of any kind installed.

how can I reduce the size without breaking the system.  I have tried DSL, Puppy, but can't get the wireless connection to work.
thanks

newbe

---

### Post by earthpigg on 2009-09-28
hi,

```
sudo apt-get clean
```

see how much space that frees up.

what that does: when you install a package, it first downloads the .deb file (Ubuntu equivalent of a setup.exe file for windows) to /var/cache/apt/archives and then installs that .deb. look around in that folder before running the command, if you like.

after it is installed, the .deb is left behind so that, if you need to, you can reinstall that package without needing to download it over again. the result is essentially that any time you have installed something via add/remove or synaptic or apt-get, it is saved in ***two*** places on your hard drive: once as a .deb in your computer's archive, and once as the installed software.

if you have reliable internet, then that functionality is almost certainly useless to you and you can go ahead and run that command as often as you like.

if you don't want to remove ***everything***, this command will only remove old or out of date .deb files:

```
sudo apt-get autoclean
```

if you want to show us your hard drive usage or have further questions about freeing up space, please post the output of this command:

```
df -Th -x tmpfs
```

---

### Post by newbemac on 2009-09-28
thanks, that reduced my used hard drive space 3.5 to 2.8 gig.

that frees up some space.

thanks again

tom

---

