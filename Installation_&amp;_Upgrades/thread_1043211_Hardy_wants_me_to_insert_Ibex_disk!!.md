---
title: "Hardy wants me to insert Ibex disk!!"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by Teabicky on 2009-01-18
Hi.  Just tried to do my usual update with the update manager when it stopped and said

> Please insert the disc labelled: Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) in drive /cdrom/

I've never had an Ibex disk and now hardy wont install its updates unless I insert this disk......Whats going on!!!:confused:

---

### Post by Teabicky on 2009-01-18
For some reason the option "**cdrom[Ubuntu 8.10 _Intrepid Ibex -Release i386 (20081029.5)]/ intrepid** main restricted" has been ticked in Software Sources, which was causing the problem.  Not sure how it happened, Ubuntu is just trying to mess with my mind.  OH well.

---

### Post by taurus on 2009-01-18
Maybe because when you installed intrepid, your network didn't work or the installer took too long to probe your network so it gave up.  As a result, it fell back to using your CD as the source instead of the repos from the net.

---

