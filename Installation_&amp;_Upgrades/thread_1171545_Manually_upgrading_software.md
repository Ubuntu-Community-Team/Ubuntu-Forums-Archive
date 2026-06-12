---
title: "Manually upgrading software?"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by stathol on 2009-05-27
I have a bit of a dilemma about Ubuntu's package management.

Jaunty's repositories currently have libvirt 0.6.1. I just found out that there's a bug in this version of libvirt that affects (well breaks, actually) live migration for kvm. This has been fixed in later versions of libvirt (the current stable release is 0.6.3).

I need this functionality for my server, so ... what should I do? If I download the libvirt 0.6.3 source, I could build it and install it manually. But then the installed version of libvirt wouldn't match the apt database anymore. I'm concerned about what effect this would have on the package management system.

Ideally, I'd like to keep the package management system "intact" so that if/when a newer version of libvirt finally makes it into the official respositories, I'll still be notified of it. That way I'll have the opportunity to upgrade/replace my source-built binaries with the ones from the repositories when they catch up with my installed version.

I know the best practice is to not screw with managed software outside of the package management system in the first place. But in this case, I don't think I really have much choice. That being the case, what's the best way to make sure that apt/synaptic/etc will continue to track updates to the libvirt related packages?

---

### Post by partsdale on 2009-05-27
good question... watching for an answer also

---

