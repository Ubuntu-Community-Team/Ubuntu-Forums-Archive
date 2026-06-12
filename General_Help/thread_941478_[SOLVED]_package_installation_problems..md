---
title: "[SOLVED] package installation problems."
date: 2008-10-08
forum: General Help
---

### Post by tacticalbread on 2008-10-08
everytime I install a package from the Add/Remove menu, or from the update menu, I get this error.

```
E: cdemu-daemon: subprocess post-installation script returned error exit status 1
E: cdemu-client: dependency problems - leaving unconfigured
```

although newly install applications work.

---

### Post by Pro-reason on 2008-10-08
Open a terminal and do this:

```

sudo apt-get update && sudo apt-get -f install

```

What is the output?

---

### Post by tacticalbread on 2008-10-08
from what I see, the same error.

```
Setting up cdemu-daemon (1.1.0-0ubuntu1) ...
 * Starting CDEmu daemon                       [[COLOR="Red"]fail[/COLOR]] 
 * Inserting vhba kernel module                [[COLOR="Red"]fail[/COLOR]]                          
                                                                         
invoke-rc.d: initscript cdemu-daemon, action "start" failed.
dpkg: error processing cdemu-daemon (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cdemu-client:
 cdemu-client depends on cdemu-daemon (>= 1.1.0); however:
  Package cdemu-daemon is not configured yet.
dpkg: error processing cdemu-client (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cdemu-daemon
 cdemu-client
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Pro-reason on 2008-10-09
I'm not familiar with the packages that you are trying to install, but try this:

```

sudo apt-get -f remove cdemu-daemon cdemu-client

```

Have you added any extra software repositories?

---

### Post by tacticalbread on 2008-10-09
that would happen with any packages I would try to install, but that seemed to fix it.

thanks. (:

---

