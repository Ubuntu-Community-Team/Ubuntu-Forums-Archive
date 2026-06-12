---
title: "I can't fix automatic updates"
date: 2006-01-25
forum: Installation &amp; Upgrades
---

### Post by catalytic on 2006-01-25
It happened again, Windows updated and killed my net, so now I am forced to use Ubuntu.
That's all good :p but I was trying to change where my updates came from, I can get them free from my ISP ftp server.

Anyway I made some changes and now, it seems to update but I get the following messages at the end.

Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


I'm willing to reinstall Ubuntu again and start over, as I really haven't done so well so far. I still can't seem to get anything to work.
I'd love some help ;) ;)

---

### Post by aysiu on 2006-01-25
Mirrormax is dead.
See the first link of my signature.

---

### Post by dcstar on 2006-01-25
[QUOTE=aysiu]Mirrormax is dead.
See the first link of my signature.[/QUOTE]
Dontcha just hate the outdated repository info that is still around in some places?....   ](*,)

---

### Post by catalytic on 2006-01-25
[QUOTE=aysiu]Mirrormax is dead.
See the first link of my signature.[/QUOTE]


Thanks that did the trick!

---

