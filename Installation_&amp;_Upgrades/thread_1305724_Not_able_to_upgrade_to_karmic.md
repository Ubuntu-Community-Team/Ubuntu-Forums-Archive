---
title: "Not able to upgrade to karmic"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by fenzik on 2009-10-30
Hi

I'm having problem in upgrading my OS to 9.10, getting the error in fetching packages from repository.

Pasted the error message for reference. Looking for someone to help in up-gradation.

```

W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages  404 Not Found
, W:Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources  404 Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

```

Thanks

---

### Post by ikt on 2009-10-30
is that when you run the update-manager or apt-get?

---

### Post by fenzik on 2009-10-30
> **ikt said:**
> is that when you run the update-manager or apt-get?

I'm getting the error when I'm trying to run **update-notifier-kde -u**

---

### Post by macogw on 2009-10-30
It looks like that Mirror doesn't have Karmic data :-/ Try opening up the Software Sources thing (may need to go through KPackgeKit to get there) and selecting a different mirror.

---

### Post by jarl on 2009-10-30
It seems like this problem:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/463435](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/463435)

---

### Post by fenzik on 2009-10-30
> **macogw said:**
> It looks like that Mirror doesn't have Karmic data :-/ Try opening up the Software Sources thing (may need to go through KPackgeKit to get there) and selecting a different mirror.

Macogw : You mean edit the source list file in /etc/apt/sources.list. Kindly advice

Thanks

---

### Post by ikt on 2009-10-30
> **fenzik said:**
> Macogw : You mean edit the source list file in /etc/apt/sources.list. Kindly advice

Thanks

You can edit that file manually or you can go through software sources (not sure of the kde equivalent) and pick one out and it will update the sources.list automagically.

---

### Post by fenzik on 2009-10-30
Yes I did and it is working now.

Thanks

---

