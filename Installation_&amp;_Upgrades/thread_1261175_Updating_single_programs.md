---
title: "Updating single programs"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by keenPenguin on 2009-09-08
Hello, 

I've been using ubuntu 8.04 for more than a year, and I would like to update several tools. I am talking about single programs, like LyX, Gimp, OpenOffice etc. of which there are already much newer version that the ones in use with ubuntu 8.04 (I am especially concerned with LyX). 

But how can I update these programs? Surely, there must be newer versions in the (standard) repositories. But when I call e.g. sudo apt-get install lyx Ubuntu tells me that "lyx is already the newest version", which it is clearly not. How can I update it anyway?

Another sort of off-topic question: From time to time, a "software update" icon appears and calls me to install some updates. But surely, this can't be all of the updates in all of the packages of the whole repository. What are these updates, then? Are they a small selection of the most important stuff handpicked by the Ubuntu team?

Thanks in advance, 

kP

---

### Post by drs305 on 2009-09-08
If you open Synaptic you can get a gui view of exactly what is happening. 

Find the package you are interested in updating in the right panel. Then check the installed version vs the latest version in the columns. If there is a newer version, right click the package and select Mark for Upgrade.

If there is no newer version but you suspect or know there should be, go to Settings, Repositories and check which repositories you have enabled in the Ubuntu Software. If you want upgrades for packages which have not been fully tested/approved, you can look at the Updates tab and select "proposed" or "backports". Hit Reload if you make any changes.

Remember that many apps are updated after an Ubuntu release goes final but will never be updated in the Ubuntu repositories for that release. You may have to upgrade to a newer release to get an "approved" package upgrade.

---

### Post by Hagar Delest on 2009-09-08
For OpenOffice.org, see [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

