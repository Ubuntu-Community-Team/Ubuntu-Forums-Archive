---
title: "Trouble with backports"
date: 2008-08-22
forum: General Help
---

### Post by MONODA on 2008-08-22
I am running ubuntu 7.10 gutsy gibbon and have enabled backports in software sources but update manager does not have any updates available for me even though non of my packages are up to date. What can I do to properyl enable backports?

---

### Post by mcduck on 2008-08-22
What do you mean with "none of your packages being up to date"?

So you mean you don't have the latest versions of packages available in Ubuntu's repositories for the Ubuntu version you are using?

Or do you mean that later versions of the programs have been released than what you have?

In general, programs are not updated after Ubuntu version ahs been released. Only security updates and fixes for more serious bugs are provided. For the latest software versions you'll have to wait until next Ubuntu release.

Backports-repository adds *some* new packages, backported from the development version of next Ubuntu release, but this is just a nice extra, aand still doesn't mean that everything would be updated, only those packages that havn't got much deependencies and that can be backported easily without affecting other packages.

---

### Post by MONODA on 2008-08-22
well then shouldnt at least things like firefox and pidgin be upgraded? as far as I know, firefox only has a few dependecies.

---

### Post by loell on 2008-08-22
these are the lists of gutsy back ported applications

[http://packages.ubuntu.com/gutsy-backports/]("http://packages.ubuntu.com/gutsy-backports/")

---

### Post by kpkeerthi on 2008-08-22
If you have any of [these]("http://packages.ubuntu.com/gutsy-backports/allpackages") installed in your set up, the versions should match with backport repository's. 

Not all applications get into the backports. Its community maintained.

---

### Post by MONODA on 2008-08-22
cool thanks for the help you guys

---

