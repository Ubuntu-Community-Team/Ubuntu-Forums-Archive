---
title: "Select repository per package?"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by Trebaruna on 2009-03-01
I'd like to be able to specify which repository is used to update a package.

Suppose I need a more recent version of g++. I enable the jaunty repository because it has what I want, but now half of my system's packages are "upgradeable".
Is there a way for me to specify additional repositories without automatically having each package considered for an upgrade? I.e. put the new repository in an ignore mode or something, and select packages individually to be kept up to date with it?

I could fetch the package by hand, I know, but if it were updated I'd need to manually get the new version.

(Please note, g++ is just an example. I'd like to know whether this functionality exists at all)

---

### Post by cariboo on 2009-03-01
I would suggest doing the updates and just pinning the applications that you don't want to update. Open System-->Administration-->Synaptic Package Manager and highlight the package you don't want to update, then select Package-->Lock Version to pin the package, so that it doesn't update.

Jim

---

### Post by Trebaruna on 2009-03-01
Thanks for your reply Jim!

If I understand your suggestion correctly, I'd have to pin all of my system's packages except for the few I do want updated with the to-be-added repository. This does not seem a desirable solution.

Perhaps I need to clarify: I'd like most of my packages to update using the "default" repositories, intrepid's main, universe, etc. A few select packages, however, I'd like to be supplied by a different repository, such as universe from jaunty. Enabling this repository should not interfere with my packages, even though it does carry newer versions of them, unless I explicitly say so for package foo.

---

### Post by tommcd on 2009-03-01
You need to be very carefull if you are trying to run a mixed system. That is, a system with packages from Intrepid *and* Jaunty. Because of the way apt handles dependencies, if the package you want from Jaunty requires a new version of libc6 or other critical packages, you could inadvertently upgrade half your packages to Jaunty and end up with a broken system.

Have you enabled the backports and proposed repos? This is one way to get newer packages and it is safer:
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

You can use apt pinning to run mixed repositories on your system. This is not commonly done on Ubuntu, but some Debian gurus use this method to run mixed (i.e., testing and unstable) Debian systems. Here is a tutorial for Debian, but the same method should work for Ubuntu using Ubuntu repos. Use at your own risk:
[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

