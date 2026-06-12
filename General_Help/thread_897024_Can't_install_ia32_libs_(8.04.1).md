---
title: "Can't install ia32 libs (8.04.1)"
date: 2008-08-21
forum: General Help
---

### Post by cdawzrd on 2008-08-21
So I just installed a fresh 8.04.1 desktop x64 (running Intel e6750, 2gb ddr2, nvidia 7900gs) and I am setting up the system.  All current updates are installed.  I am trying to get flashplayer working but ia32-libs is a prereq. for nspluginwrapper, and I can't get it to install.

Any way I try to get these installed, when it gets to trying to install ia32-libs, it fails.  Downloads the package and then starts processing it:

```
Unpacking ia32-libs (from .../ia32-libs_2.2ubuntu11_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.2ubuntu11_amd64.deb (--unpack):
 unable to create `./usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)

```

The file it's hanging up about (libGL.so.1.2) doesn't exist in that folder.

Note:  if it's important, I also had a problem where I tried using the nvidia restricted drivers, they screwed up my screen resolution so I uninstalled them using envyng and am using the stock vesa drivers now.

Note--it has been selecting amd64 even though I'm on intel64, does it matter?

After that, dpkg and apt-get are all screwed up, and I have to go through hoops to get it to do anything else (apt-get clean sometimes works).  So far, I've always been able to get aptitude working again, but whenever I try to install ia32-libs (or anything depending on it) the same thing happens.

Any advice?

---

### Post by cdawzrd on 2008-08-21
bump?

---

### Post by cdawzrd on 2008-08-30
bump

---

