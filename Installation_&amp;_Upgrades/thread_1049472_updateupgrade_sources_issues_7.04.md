---
title: "update/upgrade sources issues 7.04"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by prezbedard on 2009-01-24
I recently moved and just now got my ubuntu box set up. I'm running 7.04.

When I run either update or upgrade I am getting errors relating to sources not available.

This is what I got when I ran update manager to check for updates since its been over a month.

> [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz:](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.45 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.45 80]


so it all seems to be one source that is gone or changed. Do I need to update my sources file? What do I need to add/remove if this is the case? I'd like to get this thing updated soon so that I can in turn upgrade the distro as well.

Thanks!!

---

### Post by aheckler on 2009-01-24
Just go into **System > Administration > Software Sources** and change the server in the "Download from" box.

---

### Post by prezbedard on 2009-01-24
> **aheckler said:**
> Just go into **System > Administration > Software Sources** and change the server in the "Download from" box.

I went in and selected Main server and got the same result. I then tried find best server same thing.

> [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz:](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/main/binary-i386/Packages.gz:](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/restricted/binary-i386/Packages.gz:](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/main/source/Sources.gz:](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/main/source/Sources.gz:) 404 Not Found
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/restricted/source/Sources.gz:](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/restricted/source/Sources.gz:) 404 Not Found
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/universe/binary-i386/Packages.gz:](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/universe/source/Sources.gz:](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/universe/source/Sources.gz:) 404 Not Found
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/multiverse/binary-i386/Packages.gz:](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found


---

### Post by aheckler on 2009-01-24
It looks like your network isn't connecting. That's weird. Are you posting to UF from the same computer, or a different one?

---

### Post by avtolle on 2009-01-24
7.04 reached its end of life in October, 2008, and the repositories have been taken down. You will need to consider upgrading to at least 7.10 (I'd go to 8.04 or 8.10).

---

### Post by aheckler on 2009-01-24
> **avtolle said:**
> 7.04 reached its end of life in October, 2008, and the repositories have been taken down. You will need to consider upgrading to at least 7.10 (I'd go to 8.04 or 8.10).

Ahh, I totally forgot about that! Thanks avtolle!

---

### Post by prezbedard on 2009-01-24
> **avtolle said:**
> 7.04 reached its end of life in October, 2008, and the repositories have been taken down. You will need to consider upgrading to at least 7.10 (I'd go to 8.04 or 8.10).

Yes while searching I found this.

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

I followed the instructions and no longer have issues updating and update manager says my system ius up to date. I a, still having an issue with upgrading the distro. I am correct in that incremental upgrades are necessary? i.e I need to go to 7.10 before I an go to 8.04 etc?

Here is the error I get when I attempt a distro upgrade to 7.10 via update manager

> No valid mirror found

While scanning your repository information no mirror entry for the upgrade was found.This can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update all 'feisty' to 'gutsy' entries.
If you select 'no' the update will cancel.

When I click yes I get

> Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://old-releases.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz) 404 Not Found


---

### Post by aheckler on 2009-01-24
Honestly, I always do a fresh install when I upgrade. It feels "cleaner" that way, and it's what I would suggest.

---

### Post by prezbedard on 2009-01-24
Well after some more searching I found several places where it mentioned to remove any non-ubuntu sources such as 3rd party or restricted software. A couple more failed attempts followed. I then decided to uncheck everything, did a reload and tried again. I am now waiting on step 3 "fetching the upgrades" so far no errors. It did also mention before starting the upgrade that a bunch of packages were no longer supported. Will these be automatically removed?

Thanks!!

---

