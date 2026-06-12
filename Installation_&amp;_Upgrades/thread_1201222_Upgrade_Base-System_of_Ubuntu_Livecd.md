---
title: "Upgrade Base-System of Ubuntu Livecd"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by flouran on 2009-06-30
Hi,
I am using the Ubuntu 7.10 Livecd with some modifications I did, and I wanted to update the base-system to the most recent release of Ubuntu.
Once I have chrooted into the custom ISO's root filesystem do I use:
```

apt-get update
apt-get upgrade
apt-get dist-upgrade

```
or
```

aptitude update
aptitude upgrade

```
or neither?

---

### Post by flouran on 2009-06-30
I contacted the author of the guide I used to customize the [Ubuntu Livecd]("http://www.linuxjournal.com/article/10038"), and he said to use:
```

apt-get update
apt-get dist-upgrade

```
So I did...
After I requashed the filesystem with ```
sudo mksquashfs ./isonew/custom ./isonew/cd/casper/filesystem.squashfs
```, I got various failure messages which were of the form: ```
/certain/file not found: creating empty file
```. After I made the iso, burned it to a DVD, and I booted it up, the live cd dropped me to "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)". Does anyone know why/any remedies to this problem?

I forwarded this question to the author of the guide as well, but he has yet to respond. So please help me if you can!!!

---

### Post by flouran on 2009-06-30
Essentially, what I want to do is now that I have customized my ISO, I want to keep those customizations instead of having to apply all of them to a new Ubuntu distribution ISO image.

---

### Post by flouran on 2009-07-01
Solved it!
I will just download the new Ubuntu livecd. I found the packages I had installed from this guide: [http://www.watchingthenet.com/show-list-of-recently-installed-packages-by-date-on-ubuntu.html](http://www.watchingthenet.com/show-list-of-recently-installed-packages-by-date-on-ubuntu.html)

---

