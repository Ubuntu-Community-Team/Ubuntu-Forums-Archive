---
title: "How To Intall java On Ubuntu 7.10?"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Pedro D on 2009-06-13
Does anybody know how to install the latest version of java on Ubuntu 7.10?

---

### Post by ajgreeny on 2009-06-13
There is no support for 7.10 any more I'm afraid so I think it may be difficult to do this.  I believe there are some archived package sites for the un-supported versions so it may be possible to search for those and download the .debs, but frankly it may be easier to just accept the situation and upgrade to either 8.04 or even better, 9.04.  Do a search for **ubuntu 7.10 repositories** and you come up trumps.

---

### Post by Pedro D on 2009-06-13
OK Thank You.

---

### Post by zvacet on 2009-06-13
If you want to upgrade Gutsy to Hardy then in your source list replace all** archive.ubuntu.com** with **old-releases.ubuntu.com**

For example 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

to 

deb [http://old-releases.com/ubuntu/](http://old-releases.com/ubuntu/) gutsy main restricted

```
sudo apt-get update && sudo apt-get upgrade
```

---

