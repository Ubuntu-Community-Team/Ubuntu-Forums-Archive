---
title: "how to install build-essential?"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by dvryan on 2009-02-18
I'm trying to find/install the 'build-essential' development package for ubuntu 7.04. 

1) I tried sudo apt-et install build-essential, and it said it couldn't find the package.  How do I search for it, and if I don't have it, where can I find it online?

2) are there any other packages I'd need to install ndiswrapper?

---

### Post by oldos2er on 2009-02-18
Ubuntu 7.04 reached its end of life Oct.2008. You might want to consider moving up to 7.10 or a newer release.

---

### Post by dvryan on 2009-02-18
how would I do that?  Do I have to uninstall my current version, or can I simply download a patch?

---

### Post by Therion on 2009-02-18
> **dvryan said:**
> how would I do that?  Do I have to uninstall my current version, or can I simply download a patch?
Go to your Software Sources menu and make sure the button for Release Updgrade says "Normal Releases", see this pic (the menu is down at the bottom):

[http://reformedmusings.files.wordpress.com/2008/11/software-sources1.png](http://reformedmusings.files.wordpress.com/2008/11/software-sources1.png)

Click on "Close", "Reload" and see if you don't get a prompt about being able to update your distro.  I dunno how that's gonna work since you're on such an old version, but this is the safest way I know of if you don't want to do a clean install... Which is what I would HIGHLY recommend you do instead.

---

### Post by dvryan on 2009-02-18
I'm fine with a clean install, as long as I don't mess everything up- I'm running XP and Ubuntu 7.04 on my PC, and I just don't want to mess up the XP partition.  How would the clean install work?  Would I uninstall 7.04 first?  If so, would that mess up my partition and boot sequence?

---

### Post by Shazaam on 2009-02-18
+1 for an upgrade.
If you INSIST on using 7.04 here are two ways to install build-essential...
1. Add your Ubuntu 7.04 livecd to Synaptic (along with adding the Universe and Multiverse repo's) then search for build-essential.
2. Run this in terminal (after adding the above repo's in Synaptic)...
```
sudo apt-get install build-essential
```
For your second post...
There are many ways to upgrade (here are a few in semi-order of difficulty)...
1. Do it as Therion suggested.
2. During the partitioning phase of a fresh Ubuntu 8.10 livecd install choose "Guided-resize... " (first choice).
3. Use the Partition Editor (gparted) on the Ubuntu 8.10 livecd to manually shrink/resize the existing partitions, then do a fresh install of Ubuntu 8.10 on the unallocated space (by choosing "Manual" during the partitioning phase).
4.  Use a Ubuntu 8.10 livecd (as in #3) to delete the 7.04 partition; create an Extended partition in the unallocated space; then install Ubuntu 8.10 INSIDE of the Extended partition (choosing "Manual" once again). This gets around the 4 Primary partition limit.
If you do decide to shrink/resize the Windows partition make sure you defragment Windows first (preferably in Windows "Safe Mode").

---

