---
title: "Cannot apt-get remove libhsqldb-java, help please"
date: 2008-10-21
forum: General Help
---

### Post by Arrowx7 on 2008-10-21
Hello,
I tried installing the new openoffice3 by downloading and running a dep, but it told me some packages must be removed.  I tried removing the old open office that came with the ubuntu hardy distro, and it gave me the weird error.  I tracked it down to the following dependency:

libhsqldb-java

```
sudo apt-get remove libhsqldb-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libhsqldb-java is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cupsys (1.3.7-1ubuntu3.1) ...
chown: invalid group: `root:lp'
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can someone please help me remove this bad package?

Thanks.

---

### Post by thomas228 on 2008-10-21
not sure if this will help but you might want to read this thread for cleaning up 00o3 by using tombuntu.com script in post #2 of [http://ubuntuforums.org/showthread.php?p=6008412#post6008412](http://ubuntuforums.org/showthread.php?p=6008412#post6008412)
then try cleaning 2.4 out with post#3 of [http://ubuntuforums.org/showthread.php?t=953487](http://ubuntuforums.org/showthread.php?t=953487)
and follow up with the terminal commands in that post for installing a fresh 00o3 version.
Taking the java bit out may cause you more problems

Good luck
Tom

---

