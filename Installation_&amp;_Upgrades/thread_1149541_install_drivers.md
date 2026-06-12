---
title: "install drivers"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by volter on 2009-05-05
I download intel driver xf86-video-intel-2.7.0.tar.bz2

If you can help and tell how do I install this.

---

### Post by Mark Phelps on 2009-05-05
This is what is known as a compressed tarball file.

You need to copy the file to a directory under $Home and uncompress it by running "tar -xvfz driver xf86-video-intel-2.7.0.tar.bz2"

That will create a bunch of directories under $Home.  In one of those, you should find an "install" text file which will contain instructions on how to do the remaining steps.

But basically, what you will then be doing is running a configure file using the bash shell, which will attempt to find and resolve all dependencies.  If you've not compiled any source before, you've got your work cut out for you tracking down and resolving all the dependencies.

Once those get resolved, you will then run make and make install, which will eventually produce and install the files needed.

IF you're doing this just to install the intel video driver, it's a LOT of work just for that.  Would be better to check with the Debian search tool ([http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)), enter the package name (xf86-video-intel), select all repos, and let it find a .deb file for you.  You can download that and install it simply by right-clicking on it.

---

### Post by cariboo on 2009-05-05
THere is a ppa [here]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/"), that makes the drivers a lot easier to install, plus you get notified if there are updates.

---

