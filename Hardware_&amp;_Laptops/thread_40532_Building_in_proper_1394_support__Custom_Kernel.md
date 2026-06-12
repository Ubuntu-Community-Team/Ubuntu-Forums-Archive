---
title: "Building in proper 1394 support?  Custom Kernel?"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by dannysauer on 2005-06-09
I have some external 1394 enclosures that support 2 drives per interface - a master and a slave.  The kernel.org 2.6 kernel sees the drives fine, as do the drivers from linux1394.org.  For some reason several distributions break the 1394 support, though, and Ubuntu seems to be one of them.

I'd like to build the 1394 modules from linux1394.org's svn repository, but otherwise use the same Ubuntu kernel that I'm using.  Is there a way to maybe inject these files in to a source package and rebuild the kernel using the same otions as before?  The Ubuntu kernels apparently don't build in /proc/config.gz (which is something that would make this easier).  I just want to build these modules with the existing kernel tree...

Alternatively, if the Ubuntu folks could put together a kernel that doesn't break firewire, that'd be cool, too. :)

---

### Post by dannysauer on 2005-06-09
I suppose it'd be helpful if I mentioned that by "break 1394" I mean that only the master of the master/slave pair is recognized.  No, cable select doesn't work, and yes, I've verified that the drives work on a vanilla kernel on the same hardware (under Gentoo, though). :)

Maybe there's a general howto on how to build a kernel the "Ubuntu / Debian way"?  I know how to build a kernel (been doing that for better than a decade), but it'd be nice if I could make it tie in to the package management system properly.  I have little apt-based distro experience.

---

### Post by dannysauer on 2005-06-10
For the sake of the archives, it looks like this page might describe what to do...

[http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto](http://www.ubuntulinux.org/wiki/KernelBuildpackageDetailedHowto)

---

