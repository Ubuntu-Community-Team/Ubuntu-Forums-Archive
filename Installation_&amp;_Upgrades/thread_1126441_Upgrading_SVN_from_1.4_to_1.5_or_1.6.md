---
title: "Upgrading SVN from 1.4 to 1.5 or 1.6"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by werner bruhin on 2009-04-15
I am searching all over and have not yet found clear instructions on how one upgrades SVN 1.4 to a higher version.  Preferably 1.6 but 1.5.x would already be pretty good.

Just upgraded my Ubuntu machine to 8.10 and was hoping that this upgrades my SVN repo (which is the main use of that machine) - but no luck.

Appreciate any hints people can give me.

Werner

---

### Post by adamitj on 2009-04-15
The current repository version is 1.5.1. Did you tried an "sudo apt-get update" ?

---

### Post by SuperSonic4 on 2009-04-15
It could be as simple as ```
cd */dir*
svn update
[COLOR="Red"]./configure #or any other term like cmake ..[/COLOR]
make 
sudo make install
```

that's what it is for KMess anyway

---

### Post by werner bruhin on 2009-04-15
It did not upgrade on initial update to 8.10.

However in the mean time I ensured that I had all current updates to 8.10 (using System/Administration/Update Manager) and after having done that and done the requested (by Update Manager) reboot I did the "apt-get update" (not sure if this was needed) and I am now on 1.5.1.

Conclusion:
using update manager or apt-get update will get you up to the version of SVN which is included in the version of Ubuntu (for 8.10 this is 1.5.1), if you want to be more leading edge then the steps must be more involved.

Maybe another day I will try to find out, but for I need it I am fine.

Thanks for the different responses.
Werner

---

