---
title: "Upgrading and keeping /home"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by ishkabibble on 2009-01-19
I'm currently using Hardy Heron release.  I have a CD for the Ibex release, so I'm looking to upgrade.  I've set this computer up with a separate /home partition as was suggested previously.  When I start the fresh install, will it recognize the /home directory?  What should I expect to see?  This is the first time I've upgraded this way.

---

### Post by taurus on 2009-01-19
If you do a fresh install of intrepid, pick the Manual option when you get to the partition screen.  Then, mount the right partition to / and format it.  Now, you want to mount your old /home partition to /home but do not format it if you want to keep all your files on /home.  That's all there is to it.

---

### Post by ishkabibble on 2009-01-19
Excellent!  It worked except for the other users.  How do I add them back?  I tried using the Users and Groups app and was told I couldn't add one where a directory already exists.

---

