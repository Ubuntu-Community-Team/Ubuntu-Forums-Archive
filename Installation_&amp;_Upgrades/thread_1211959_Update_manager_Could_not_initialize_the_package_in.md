---
title: "Update manager: Could not initialize the package information"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by kerttu on 2009-07-13
Hi,

I'm in trouble with my package manager. When I start it, it says:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Opening /etc/apt/sources.list.d/medibuntu.list - ifstream::ifstream (13 Permission denied), E:The list of sources could not be read.'

Please, help!

-Kerttu

---

### Post by csabo2 on 2009-07-13
what are the permissions on that directory and file?

---

### Post by puddinhead3 on 2009-07-17
Hi.  I just upgraded from 08.10 yesterday and observed the same problem this morning.

# update-manager
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 54 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

# ls -ld /etc
drwxr-xr-x 142 root root 12288 2009-07-17 10:19 /etc
# ls -ld /etc/apt
drwxr-xr-x 4 root root 4096 2009-07-16 17:44 /etc/apt
# ls -ld /etc/apt/sources.list
-rw-r--r-- 1 root root 3037 2009-07-16 17:44 /etc/apt/sources.list

# update-manager -d
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 54 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

# grep -n firefox sources.list
54:deb [http://mozilla-mirror.3347.voxcdn.com](http://mozilla-mirror.3347.voxcdn.com) firefox-3.5

---

### Post by puddinhead3 on 2009-07-17
never mind.  this is my fault.
from the GUI, System/Administration/Software Sources, select Third-Party Software tab.  I was trying to install the new firefox but it isn't ready yet and I neglected to clean up afterwards.

removing that entry via the UI, I can now execute update-manager no problem.

---

### Post by apax on 2009-12-12
Hi -- I just encountered the same problem.  I had created a new /etc/apt/sources.list.d/medibuntu.list based on instructions from [http://ctevisions.com/2009/10/31/play-dvds-with-ubuntu-9-10karmic/](http://ctevisions.com/2009/10/31/play-dvds-with-ubuntu-9-10karmic/).  The instructions were all right, but I had a default umask of "66" which caused the file to become unreadable to users other than root.  Fix with:

sudo chmod 644 /etc/apt/sources.list.d/medibuntu.list

That did it for me.

---

### Post by vmguru007 on 2011-06-15
Hi,

I have just faced a similar problem with Ubuntu 11.04 and the following article helped me fix it. I believe this problem will be popular as many of us are upgrading to 11.04, so I thought I will share the fix I found at the following article.

[ Ubuntu Update Manager could not initialize the package information Article]("http://www.linux2aix.com/linux/ubuntu/ubuntu-1104-update-manager-could-not-initialize-the-package-information.html")

I hope the new unity GUI get stabilized and improved soon. Although over all it seems nice, it still need massive improvements :).

I hope this help, & make me contribute to this great community.

Enjoy,
Erick

---

