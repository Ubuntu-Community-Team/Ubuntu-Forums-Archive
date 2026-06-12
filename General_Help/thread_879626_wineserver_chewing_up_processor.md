---
title: "wineserver chewing up processor?"
date: 2008-08-04
forum: General Help
---

### Post by sdowney717 on 2008-08-04
I noticed computer just bogged after installing ie4linux 6.0

Curious if this happens to everyone

---

### Post by mygravity on 2008-08-11
Yes, I experience the same problem when running IE6 using ies4linux (version 2.99.0.1) on Ubuntu 8.04 LTS Desktop Edition. :(

Other users have also reported this:
[http://ubuntuforums.org/showthread.php?t=799575](http://ubuntuforums.org/showthread.php?t=799575)

Did not have the same problem when using ies4linux on Ubuntu 6.

---

### Post by mygravity on 2008-08-11
There is some discussion of the issue here:

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895)

Unfortunately doesn't seem to offer a fix. It just mentions adding some commands to the end of the ie6 script to kill the wineserver.

---

### Post by tjwilli on 2009-09-20
> **mygravity said:**
> There is some discussion of the issue here:

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895)

Unfortunately doesn't seem to offer a fix. It just mentions adding some commands to the end of the ie6 script to kill the wineserver.

I installed ies4linux today and have had the same problem about having to kill the wineserver and also IE6. I've found out that if I am *not* connected, than IE6 closes fine and the wineserver also closes normally. (Browsers normally aren't much good unless you're connected to the internet though.)

---

