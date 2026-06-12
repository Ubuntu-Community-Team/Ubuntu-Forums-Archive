---
title: "Network broken after upgrade"
date: 2008-11-09
forum: General Help
---

### Post by beebee on 2008-11-09
I'm just now getting around to upgrading from Feisty (7.04).  I came across a post that made it sound like I needed to upgrade to Gutsy (7.10) before I could upgrade to 8.10.

After upgrading to Gutsy, I have no network access at all.  Before the upgrade, my nic was working fine with the r8169 driver.  The driver is getting loaded.

Incidentally... during the upgrade, I kept a copy of every notice.  After rebooting, I discovered that the upgrade overwrote /etc/network/interfaces with no warnings whatsoever.

I'm not new to Linux, but am relatively new to Ubuntu.  I need some clues as to where I should start looking.

Thanks.

:bb

---

### Post by beebee on 2008-11-09
I found a workaround -- posting in case anyone else has the same problem.

Seems like most people who have this sort of problem were able to fix it using Globemaster's suggestion at [http://ubuntuforums.org/showthread.php?t=671614&highlight=r8169+gutsy](http://ubuntuforums.org/showthread.php?t=671614&highlight=r8169+gutsy).  That approach did not work for me.

However, there are instructions at [http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem](http://adam.rosi-kessel.org/weblog/2008/06/21/a-much-simpler-fix-for-the-r8169-link-down-problem) which did work.

:bb

---

