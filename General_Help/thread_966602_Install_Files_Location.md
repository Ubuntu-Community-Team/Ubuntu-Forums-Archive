---
title: "Install Files Location"
date: 2008-11-01
forum: General Help
---

### Post by jadhav333 on 2008-11-01
1) Where do the installed files (binaries, data files, configs, preferences, etc..) go on the harddisk? 

2) Is there any logic in the way the files are distributed in different locations?

3) How/where should we install tar.gz files (not from ubuntu repositories)?

4) Where are the locally downloaded files by the synaptic manager located? Can we safely delete them, once the installations are done?

Regards
jadhav333

---

### Post by oldos2er on 2008-11-01
Google "linux file system structure" to find answers to your first two questions. Where you install tar.gz files depends on what's in them. Assuming it's source code, when you run "make install" they will be installed like any other package. 

 apt stores its packages in /var/cache/apt/archives . Run the command "sudo apt-get clean" to remove them.

---

### Post by geirha on 2008-11-01
Wikipedia has a nice page on it: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Also, to see where a specific package installs its files, run this in a terminal
```
dpkg -L *packagename*
```

---

### Post by cariboo on 2008-11-01
You could also go to System-->Administration--Synaptic Package Manager, highlight the package you installed, then click Properties-->Installed Files. This will show you where the files from the installed package are located.

Jim

---

