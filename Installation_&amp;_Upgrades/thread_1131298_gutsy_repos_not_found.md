---
title: "gutsy repos not found"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by jstroot on 2009-04-20
The gutsy main, universe, multiverse, and restricted repos
at either 
[http://archive.ubuntu.com/ubuntu/dists](http://archive.ubuntu.com/ubuntu/dists)
or
[http://us.archive.ubuntu.com/ubuntu/dists](http://us.archive.ubuntu.com/ubuntu/dists)
[http://de.archive.ubuntu.com/ubuntu/dists](http://de.archive.ubuntu.com/ubuntu/dists)

are missing. 

[http://it.archive.ubuntu.com/ubuntu/dists](http://it.archive.ubuntu.com/ubuntu/dists)
still has them.

Was this planned? When can they be expected to return?

-jstroot

---

### Post by Darael on 2009-04-20
Gutsy reached the end of its support cycle two days ago.  The repositories are being moved to old-releases.ubuntu.com instaed of *.archive.ubuntu.com and there will be no further updates to Gutsy.  It's advisable to upgrade to a still-supported version - Hardy will be supported for another two years, or you could follow the upgrade path through Hardy and Intrepid and go as far as Jaunty in a couple more days (or the release candidate now, if you like).

EDIT: for gutsy-to-hardy upgrades, see [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades) though you may have to change your /etc/apt/sources.list to point to the new location of the repos.

---

### Post by jstroot on 2009-04-20
Thanks for the info! Much obliged!

---

### Post by Darael on 2009-04-20
One more thing - if you're still running Dapper on your desktop as your user data suggests, it'll reach End-of-Life (EOL) in June.  It's a good idea to upgrade at least to Hardy at his point in that case - or anyway, in fact.  Hardy is the next LTS release, and will be supported for two years from now or four on the server (three or five years from release, respectively).

If you do still have a Dapper system that needs upgrading, the same link I cave you before should cover it.

Oh, and: > Thanks for the info! Much obliged!
Not at all. Happy to help.

---

### Post by dveej on 2009-04-21
I have a related problem: I just upgraded successfully my gutsy to hardy, but when I run Update Manager or Synaptic, it always fails to fetch the repositories. Can anyone help with this?

---

