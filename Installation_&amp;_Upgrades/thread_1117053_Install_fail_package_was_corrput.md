---
title: "Install fail: package was corrput"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by Flatron on 2009-04-05
I'm trying to install Ubuntu 8.10 Server Edition. I downloaded the image twice, and tried to write about 4 times to 2 different dvds (with speed 4x, 2x, 2.6x) and I even tried to install with network booting as explained here: [http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive](http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive)

Every time while the base system is installing, I got a message: Debootstrap warning

Warning: xy was currupt

Where xy is a package's absolute path, but the package is not the same in different installations. Now, with network boot, the first is the libssl0.9.8_0.9.8g-10.1.ubuntu2_amd64.deb
When I press Continue, it says Couldn't download package: libssl0.9.8, and then a series of similar messages come up.

With dvd install, I got on corrupt message, and one "could'n t find" message, and again and again several times, before it said the install failed.

---

### Post by Partyboi2 on 2009-04-05
Did you check that the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") matches after you downloaded the iso?

---

### Post by Flatron on 2009-04-05
Yes, both matched, and I did a Self check before install in each case.

---

