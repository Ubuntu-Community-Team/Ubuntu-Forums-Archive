---
title: "multiple partitions for single Ubuntu install"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by Rubicon421 on 2009-01-14
I've read about several people setting up ubuntu with multiple partitions for a single install, so they can use one for root, one for home, user, etc...

What is the advantage to this setup?
If I do it, how many partitions should I make? Should I create them with Windows before I begin installing ubuntu?

---

### Post by Pumalite on 2009-01-14
With Vista; allocate space for Ubuntu first:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
With XP; you can use the Live CD; go 'Manual':
10 to 20 GB for '/'
The rest minus 1.5 of your RAM for /home
1.5 of your RAM for /swap

---

### Post by Partyboi2 on 2009-01-14
The advantage of having /home on its own partition is that if you ever need to reinstall Ubuntu at any time  everything eg videos, personal data etc on your /home parition will not be touched.
To setup a /home partition you can choose manual when it comes to the partitioning stage of the install and create a ext3 partition with the mount point set to /home

---

