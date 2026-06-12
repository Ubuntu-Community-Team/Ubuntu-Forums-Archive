---
title: "Debian package generation"
date: 2008-11-03
forum: General Help
---

### Post by maddis on 2008-11-03
I'm been generating my own packages using these instructions. [http://ubuntuforums.org/showthread.php?t=51003]("http://ubuntuforums.org/showthread.php?t=51003")

Everything is working fine ie. I was able to make the package. My package is new usplash images so I need to change link to point to my usplash, run dpkg-reconfigure for linux-image and it would be good to be able to restore the original link if/when the package is removed.

The problem now is that I'm not sure where I should put those commands. Also it seems that I need root privileges when generating the package because it runs those commands on that machine I use to generate the package. It's not good so I'm guessing I need another machine that I use to test/generate the packages if I don't want to mess up the one I use to develop them.

Probably all those problems are already solved, but I just don't know it.

---

### Post by maddis on 2008-11-04
*This problem was solved. Own mistake. :rolleyes: *

---

### Post by maddis on 2008-11-06
Hi,

Still need help about commands that is run during package installation phase if there is any possibility. I need to be able to modify few configuration file as well as run some other commands, but I'm not sure how to make that happen in debian package.

This is more like programming help, but I'd appreciate if someone would at least point to right direction.

---

