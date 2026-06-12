---
title: "&quot;Authentication failed&quot;: missing libgdbm.so.2"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by jonathanhayward on 2009-10-29
I'm running Jaunty, and both the update manager and do-release-upgrade are failing. Adding a -d doesn't change this; the problem appears to be that something requires a libgdbm.so.2 and is not accepting the installed libgdbm.so.3. Any wisdom?

```
root@jonathanscrossing ~ # do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'karmic.tar.gz'
authenticate 'karmic.tar.gz' against 'karmic.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 127
Debug information: 

gpg: error while loading shared libraries: libgdbm.so.2: cannot open shared object file: No such file or directory


Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server. 
root@jonathanscrossing ~ # 
```

---

### Post by jonathanhayward on 2009-10-29
I found the answer, I think. There was an old version of gpg stored under my home directory (in my search path), and the update manager pulled the old version from my path and bypassed the binary installed by the distribution.

---

