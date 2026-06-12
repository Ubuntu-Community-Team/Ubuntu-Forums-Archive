---
title: "Upgrading to 8.10 may ruin desktop effects"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by Dustin2128 on 2009-03-11
when I was in the process of upgrading to 8.10, I got this message about half way through, ah lost it. Anyway, it said that dekstop effects may not work/be greatly reduced because the driver for my geforce 4 isn't avalible in 8.10. Question number one is: If I upgrade to 8.10 will there be a better driver avalible?  and if not, what's the point of dropping the driver. Also, could I just keep the driver some how?

---

### Post by Neo_The_User on 2009-03-11
MAY. not will. mesa can host desktop effects. it doesnt need proprietary drivers.

---

### Post by avtolle on 2009-03-11
> **Dustin2128 said:**
> when I was in the process of upgrading to 8.10, I got this message about half way through, ah lost it. Anyway, it said that dekstop effects may not work/be greatly reduced because the driver for my geforce 4 isn't avalible in 8.10. Question number one is: If I upgrade to 8.10 will there be a better driver avalible?  and if not, what's the point of dropping the driver. Also, could I just keep the driver some how?
See [http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support) for a bit more full explanation. Neo-User would be the one to advise more on the mesa driver (different than the default nv driver you will be "offered" in the upgrade) and how to get it in use, which I expect involves the editing of the /etc/X11/xorg.conf file to change drivers from nv to mesa.

---

### Post by Neo_The_User on 2009-03-11
> **avtolle said:**
> See [http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support) for a bit more full explanation. Neo-User would be the one to advise more on the mesa driver (different than the default nv driver you will be "offered" in the upgrade) and how to get it in use, which I expect involves the editing of the /etc/X11/xorg.conf file to change drivers from nv to mesa.

k thats what i said!

---

