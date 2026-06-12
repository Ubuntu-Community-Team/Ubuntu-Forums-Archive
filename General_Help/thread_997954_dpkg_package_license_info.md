---
title: "dpkg package license info"
date: 2008-11-30
forum: General Help
---

### Post by ttys0 on 2008-11-30
I've been looking at dpkg-query, and can't find how to show the licensing information for particular packages.

License is not one of the options in the customized show format list, and I haven't been able to find out how to use other tools such as apt-cache to show the license information for a particular package.

Any hints on where to look for getting this information for installed packages would be greatly appreciated.

-Sean

---

### Post by nshenry03 on 2011-03-08
Try this:

dpkg --license oracle-xe-universal_10.2.0.1-1.0_i386.deb | less

---

