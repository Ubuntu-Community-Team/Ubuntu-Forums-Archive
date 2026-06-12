---
title: "Creation of deb package (problems with &quot;Provides&quot;)"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by liquidator87 on 2009-02-22
Recently I compiled x264 from source, with the executable and the shared library, which is at revision 66... So I removed the repo version (rev 59), and I created a deb package, named "x264"... no problems.
But now, if I want to install a package which depends on libx264-59, I'm told to install that package, even though I've specified that my package provides libx264-59 in the control file of the deb...
Any idea?

---

