---
title: "how to restore installation to &quot;vanilla&quot; state"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by ittayd on 2009-05-30
Hi,

My laptop started with Ubuntu 7.04 and has gone several distribution upgrades to 9.04. In order to fix incompatibilities, I have also changed many /etc files. 

I have some major issues that prevent me from working (computer freeze, can't suspend to ram), so as a last resort I want to try to reset 9.04 to a "vanilla" state, without all the hacks I've done through the years. I obviously don't remember them all.

What is the best approach here? Re-install (how do I maintain the same package set as I have now, don't want to need to reinstall all of them)? dpkg reconfigure -a?

Thank you,
Ittay

---

### Post by Mark Phelps on 2009-05-31
To maintain the same package set, check out AptOnCD.  It provides the ability to create a CD containing all the packages you added since installation.  You can use that CD after you reinstall to reinstate your packages. However, I don't know if it will pick up the ones you upgraded as well.

The link is below:

[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

