---
title: "Upgrading from a custom DVD"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by ngolian on 2009-04-03
I installed Ubuntu on both my sisters' PCs, and I'd like to upgrade them to Jaunty. The trouble is, they both have slow and/or download-limited Internet connections. The last time I upgraded one of them I sped things up a little by using the alternate install CD, but it still took a few hours to download additional packages.

Is it possible to get update-manager to just list the packages it would download without actually downloading them, so I can download them at my house and burn them to DVD? And how can I set the DVD up so it can be used as a source of packages? Or would simply dropping the files into /var/cache/apt/archives on the target PCs do the trick?

---

### Post by ngolian on 2009-05-24
I'd better let people know, simply dropping the packages into /var/cache/apt/archives does work. I used apt-get dist-upgrade -s to get a list of package names. The upgrader still needed to download a few things, but it still saved several hours even compared to using the official CD.

---

