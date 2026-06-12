---
title: "VM login window resolution issue Jaunty"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by L0wCr4WL on 2009-04-25
I just installed 9.04 Jaunty and it's running in a VMWare Fusion 2.0 VM on Mac OS X 10.5.6

No problems with the install but the login spalsh screen is not the correct width of 1440 x 900 (please see screenshot). Once loged in however, VMWare Tools (the latest are installed) takes over and ensures the correct resolution is set.

I tried to find the answer on these forums and VMWare's own and I am not sure where to look. Is this in the XConf file, VMX for the VM or somewhere else? Can this even be fixed?

Thanks!:confused:

---

### Post by robolange on 2009-08-01
This is a more important issue than it initially seems.  When X11 first starts up, some information about the screen geometry (DPI? something else?) is recorded based on the initial screen resolution.  Some older GUI toolkits seem to use this information to choose the size of the fonts.  When the user changes screen resolution after logging in, this information does not seem to be updated, so these older apps open up with comically large fonts, rendering them unusable.

If I manually set the screen resolution in xorg.conf, so that the user resolution never needs to be changed, then the older apps open with normal sized fonts.  But I don't like editing xorg.conf, because that's an archaic method of configuring an operating system, and I thought all of these auto-config advances were supposed to obsolete that.

I think that this problem affected older versions of emacs, but I don't have any pre-GTK emacs installed anymore.  It also currently affects a proprietary tool that I have to use.

---

