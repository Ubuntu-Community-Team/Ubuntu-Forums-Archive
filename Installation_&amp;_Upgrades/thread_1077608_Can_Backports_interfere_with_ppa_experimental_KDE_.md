---
title: "Can Backports interfere with ppa experimental KDE 4.2?"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by vayu on 2009-02-22
I've received several updates from backports after I had upgraded to KDE 4.2 and was wondering (as the update messages scroll by) if anything might be conflicting or overwriting something newer.

# Kubuntu Experimental Software Personal Package Archive (PPA) repository
deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main

---

### Post by snova on 2009-02-22
> **vayu said:**
> I've received several updates from backports after I had upgraded to KDE 4.2 and was wondering (as the update messages scroll by) if anything might be conflicting or overwriting something newer.

If anything were conflicting, you would know. And I don't think apt will allow an older version of a package to overwrite a new one (not without forcing it).

I enabled both, and have no problems.

---

