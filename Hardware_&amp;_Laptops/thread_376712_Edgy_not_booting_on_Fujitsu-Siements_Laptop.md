---
title: "Edgy not booting on Fujitsu-Siements Laptop"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by rem on 2007-03-05
Hi guys,

Just bought a laptop [http://ubuntuforums.org/showthread.php?t=376005&page=2](http://ubuntuforums.org/showthread.php?t=376005&page=2). Had a good offer from one of the local stores. Got home, run Edgy Live CD, everything went just fine with the installation but when finished, doesn't want to boot. Repeated this operation twice and still nothing. I just read in the previous post, somebody had the same problem with a Fujitsu laptop except mine is P4 Mobile and don't wanna anything else but Ubuntu :D

Thanks a lot!

---

### Post by rem on 2007-03-05
Fixed!

It was so simple! I didn't set the partition active when installed (don't get it why not active by default???). So, I fired it up with the LiveCD then mounted the installed linux partition and flagged it boot with GParted! It works now! :guitar:

---

