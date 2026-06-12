---
title: "recompiling ubuntu source package"
date: 2008-11-18
forum: General Help
---

### Post by igknighted on 2008-11-18
I need to apply a patch to the intel driver in ubuntu, and then recompile the package.  I have downloaded the source package and made the required changes, now I need to rebuild the package.  I have tried ./configure, make, make install and it seemed to install, but the driver simply doesn't work now.  How can I rebuild the package and install via dpkg?

---

### Post by Yellow Pasque on 2008-11-18
These directions always worked for me: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
I follow 'The Old-Fashioned Debian Method'.

---

### Post by igknighted on 2008-11-18
> **Temüjin said:**
> These directions always worked for me: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
I follow 'The Old-Fashioned Debian Method'.

I'm not recompiling a kernel, just the xserver-xorg-video-intel package.

I used apt-get source to download the source, I removed and --purged the old driver, I modified the file I needed (i830_lvds.c), and now I need to install the modified source package.  I would like to package and install via dpkg, as when I tried "./configure, make, sudo make install", the intel driver simply wont work at all (as opposed to before where X loaded with a blank screen).  Even after moving the modules from /usr/local/lib/ to /usr/lib/ where the rest of them are.

Anyways, my goal now is to simply rebuild the package and install that way.  Anyone know how I can do that?

---

### Post by Crafty Kisses on 2008-11-18
I'm guessing you have the following package installed right?
```
sudo apt-get install build-essential
```

---

### Post by igknighted on 2008-11-18
> **Codename said:**
> I'm guessing you have the following package installed right?
```
sudo apt-get install build-essential
```

yes.

As I said, it compiled fine, no errors.  It just didn't work once compiled.

After reinstalling Ubuntu and removing the intel driver right away, then compiling and installing the new one before any updates (this was off the beta), it worked.  But I would still like to know how to build the deb instead of just compiling it.

---

