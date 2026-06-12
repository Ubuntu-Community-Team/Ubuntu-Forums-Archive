---
title: "gimp version after Intrepid update"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by fatnic388 on 2009-01-27
Hi. I've recently updated to 8.10 from 8.04 and so far not had any problems. However I'm currently trying to update GIMP to 2.6 from 2.2. As you can see from this terminal output I'm getting different results from aptitude and GIMP itself.
```

dave@laptop:~$ gimp -v
GIMP version 2.2.11
dave@laptop:~$ apt-cache policy gimp
gimp:
  Installed: 2.6.3-1ubuntu1~intrepid1
  Candidate: 2.6.3-1ubuntu1~intrepid1
  Version table:
 *** 2.6.3-1ubuntu1~intrepid1 0
        500 http://gb.archive.ubuntu.com intrepid-backports/main Packages
        100 /var/lib/dpkg/status
     2.6.1-1ubuntu3 0
        500 http://gb.archive.ubuntu.com intrepid/main Packages

```
GIMP say's it's at version 2.2 and apt says 2.6. Also GIMP loads up version 2.2.

So how can I get it to update?!?

---

