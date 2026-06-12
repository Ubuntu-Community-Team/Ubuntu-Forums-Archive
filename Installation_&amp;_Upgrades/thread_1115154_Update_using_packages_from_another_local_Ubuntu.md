---
title: "Update using packages from another local Ubuntu"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by projectshave on 2009-04-03
I've got a few Ubuntu systems running. They want to update mostly the same packages. Currently, each machine downloads the packages from the central Ubuntu repository. I'd rather have each machine check the others on my local network to see if they already have the package. That way I can update all my systems but only download a package once. How do I set that up with apt-get?

Thanks.

---

### Post by Partyboi2 on 2009-04-03
You could use apt-cacher
[http://sandeep.co.in/2008/10/30/updateupgrade-multiple-ubuntu-pcs-with-apt-cacher/](http://sandeep.co.in/2008/10/30/updateupgrade-multiple-ubuntu-pcs-with-apt-cacher/)
[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)

Or aptproxy
[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)

---

