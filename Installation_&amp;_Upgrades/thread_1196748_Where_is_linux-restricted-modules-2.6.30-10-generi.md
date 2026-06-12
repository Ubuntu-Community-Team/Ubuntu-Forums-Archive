---
title: "Where is linux-restricted-modules-2.6.30-10-generic?"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by GreatEmerald on 2009-06-25
I have installed the Linux kernel 2.6.30-10 into my Xubuntu 9.04 Jaunty due to better internet driver support, but I have encountered some problems while trying to free up space on my drive and uninstall the old unused kernels.
The problem is that there is no linux-restricted-modules-2.6.30-10-generic package in the package manager! In fact, it's not even mentioned on Google! That means that after I uninstalled the kernels 2.6.28-11 and 2.6.28-13, Xubuntu no longer boots - that is, it works, but due to the lack of restricted modules the screen shows nothing and the wireless internet card doesn't work... The strange thing about this is that if I use dpkg to install linux-restricted-modules-2.6.28-11-generic_something from a .deb file, the installation partially fails (because I no longer have the 2.6.28 kernel), but after that restricted modules work correctly and let me boot; though as it's a failed install, apt-get won't let me install anything new without removing that partial install... And that would mean it won't boot again...

So, is there any place I could get restricted modules for 2.6.30-10 or 2.6.30-8, so I wouldn't need the old kernels lying around?

Meanwhile, I'll use the 2.6.30-8 kernel (which also doesn't have the restricted modules, but seems to make use of older restricted modules just fine) and have 2.6.28-13 installed for restricted modules support.

---

### Post by jimv on 2009-06-25
How did you install 2.6.30?  It's not a Jaunty package...

---

### Post by The-Don on 2009-06-25
2.6.30 is available as a vanilla kernel ONLY. In other words, [www.kernel.org](www.kernel.org) contain the base templates for distros. So, the Ubuntu developers grab the vanilla kernel and then customise some areas here and there to make it perfectly compatible with Ubuntu's mechanics. Sure, you can compile it yourself - but at the risk (if inexperienced) of breaking your system.

Ubuntu 9.10 released Oct 29th this year will have 2.6.30 built into it, so there's no rush to manually upgrade yourself. Between now and then the developers do release minor updates to the vanilla kernel and right now were on 2.6.28.13.

I would suggest leaving the kernel as it is unless you absolutely require USB 3.0 support and other specific driver updates.

---

### Post by GreatEmerald on 2009-06-25
That's strange - I have them in my Synaptic list, and I have only stock repositories and X server updates in my package sources. And both 2.6.30 kernels are marked with the Ubuntu logo. Properties also say (Jaunty) at the end of the version...

---

### Post by The-Don on 2009-06-25
Now that is weird, not in my list - don't suppose you have all the deb-src's active or added non-default sources?

Confused :confused:

I just double-checked and 9.04 definitely doesn't have anything later than 2.6.28-13. Then again, maybe Xubuntu has a new kernel version, I wouldn't know though to be honest :\

---

### Post by GreatEmerald on 2009-06-26
My current active repositories are:
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty, WINE repository
[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty, XOrg Edgers
[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty, source of XOrg Edgers
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty, X Updates
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty, source of X Updates
[http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free, Skype

---

### Post by Hitman_Forhire on 2009-06-28
I checked out the package info on a couple of those extra repo's that you listed there and it seems that this:

[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty, XOrg Edgers

repository is the one with the kernel on it maybe. If not I'm not sure. I've been interested in finding the latest stable working build of it catere for Ubuntu on a trusted repo.So if anyone was asking because they wanted to add it there ya go, and if you were interested in avoiding it, all the same. I was just curious myself :D.

---

