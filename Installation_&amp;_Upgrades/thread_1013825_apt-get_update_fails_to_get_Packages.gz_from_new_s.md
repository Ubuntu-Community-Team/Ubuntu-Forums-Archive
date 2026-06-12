---
title: "apt-get update fails to get Packages.gz from new souces"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by mjoolnir on 2008-12-17
Whenever I add any new repository (for WINE or Spring in this case) apt-get fails to get Packages.gz from the server. When I do sudo apt-get update I get this back at the end: ```
W: Failed to fetch http://ppa.launchpad.net/spring/ubuntu/dists/intrepid/main/binary-i386/Packages.gz  404 Not Found [IP: 146.137.96.7 80]

W: Failed to fetch http://ppa.launchpad.net/spring/ubuntu/dists/intrepid/main/source/Sources.gz  404 Not Found [IP: 146.137.96.7 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```
I can fetch the archive with wget, so the server isn't down. I made a file called /etc/apt/sources.list.d/springproject.list the contents of which are ```
deb http://ppa.launchpad.net/spring/ubuntu intrepid main
deb-src http://ppa.launchpad.net/spring/ubuntu intrepid main
```
Is there a reason for this? I tried putting the repositories in sources.list also but it did the same thing.

---

### Post by mjoolnir on 2008-12-18
bump

---

