---
title: "[SOLVED] Package manager problem"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by elzorroviejo on 2009-01-01
I am running Ubuntu 8.10 on Linux kernel 2.6.27.7. My first problem is with the update manager. Right now it is telling me that my system is up-to-date with the last update being 15 days ago. However, when I manually tell it to go check, the load bar gets about 1/3 of the way across, and then it pops up with a bunch of error messages--all of which say:

[CENTER]W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

[/CENTER]

Any comments/suggestions/fixes??

Thanks...

---

### Post by Rocket2DMn on 2009-01-01
Sounds like a problem with the mirror you are using, you can try a different mirror from System->Administration->Software Sources.  Change your mirror from the "Download from:" dropdown box.  Then try your update and upgrade again.

---

### Post by Copernicus1234 on 2009-01-01
There is no host on the Internet named archive.ubuntu-rocks.org. I think you have probably typed in the wrong name for your update mirror.

Go to System -> Administration -> Software Sources and select another update server.

Edit: I wasnt quick enough. :)

---

### Post by elzorroviejo on 2009-01-01
There were over 200 updates available to me. I think this happened when I upgraded to both Intrepid and the 2.6.27.7 kernel at the same time. Because I never changed my package manager...at least not that I can remember doing...However, the problem now seems to be solved. Thanks again...

---

