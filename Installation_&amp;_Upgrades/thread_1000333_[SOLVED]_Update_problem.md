---
title: "[SOLVED] Update problem"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by ayako0chan on 2008-12-02
I am trying to update my computer using the update manager.  However, when it tries to download packages, it stops at one package and produces the following error.

> W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/intrepid/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/intrepid/Release.gpg](http://packages.freecontrib.org/ubuntu/freecontrib/dists/intrepid/Release.gpg)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/intrepid/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/freecontrib/dists/intrepid/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/freecontrib/dists/intrepid/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/freecontrib/dists/intrepid/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://mirror.ubuntulinux.nl/dists/intrepid-seveas/all/binary-i386/Packages.gz](http://mirror.ubuntulinux.nl/dists/intrepid-seveas/all/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://mirror.ubuntulinux.nl/dists/intrepid-seveas/all/source/Sources.gz](http://mirror.ubuntulinux.nl/dists/intrepid-seveas/all/source/Sources.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


How can I fix this?  Thanks for all help in advance.

---

### Post by Pumalite on 2008-12-02
System>Administration>Software Sources>Third Party>Tick off the offending repos.
Then:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by ayako0chan on 2008-12-02
Thank you!  That fixed it!

---

