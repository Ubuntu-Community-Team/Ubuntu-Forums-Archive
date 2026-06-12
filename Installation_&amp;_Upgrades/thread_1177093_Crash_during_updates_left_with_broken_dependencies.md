---
title: "Crash during updates left with broken dependencies"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by Don Giovanni on 2009-06-03
This morning i was updating through the update manager and my system locked up, I tried to let it go on its own but in the end I had to hard reset. I tried to complete the updates but it returned with dependency errors

sudo dpkg --configure -a
gives me the following
```
Setting up libsqlite3-0 (3.6.10-1ubuntu0.2) ...
dpkg (subprocess): unable to execute post-installation script
: Exec format error
dpkg: error processing libsqlite3-0 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up foomatic-db-engine (4.0.0-0ubuntu6.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing 
foomatic-db-engine (--configure):
subprocess post-installation script returned error exit status 2

dpkg: dependency problems prevent configuration of evolution-plugins:
evolution-plugins depends on libsqlite3-0 (>= 3.6.10); however:
  Package libsqlite3-0 is not configured yet.

dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on libsqlite3-0 (>= 3.6.10); however:
 Package libsqlite3-0 is not configured yet.

dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
Setting up cron (3.0pl1-105ubuntu1.1) ...

dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing cron (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of evolution-dbg:
 evolution-dbg depends on evolution (= 2.26.1-0ubuntu2); however:
  Package evolution is not configured yet.

dpkg: error processing evolution-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libsqlite3-0
 foomatic-db-engine
 evolution-plugins
 evolution
 cron
 evolution-dbg

```

---

### Post by KWhistle on 2009-06-04
Same here.

---

