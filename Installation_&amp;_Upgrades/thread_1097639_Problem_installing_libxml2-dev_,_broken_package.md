---
title: "Problem installing libxml2-dev , broken package"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by WiryLattice on 2009-03-16
Trying to install libxml2-dev but it depends on an older version of libxml:

$ sudo apt-get install libxml2-dev
The following packages have unmet dependencies:
  libxml2-dev: Depends: libxml2 (= 2.6.32.dfsg-4ubuntu1) but 2.6.32.dfsg-4ubuntu1.1 is to be installed
E: Broken packages


I managed to find this libxml2-dev source [https://dogfood.launchpad.net/ubuntu/+source/libxml2/2.6.32.dfsg-4ubuntu1.1](https://dogfood.launchpad.net/ubuntu/+source/libxml2/2.6.32.dfsg-4ubuntu1.1), but i am uncertain as to how to go about installing it. Shouldn't there be a .deb package of this somewhere? 


cat /etc/apt/sources.list | grep -v '#'
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse



After looking at posts with similar problems i have found that this seems to be a relevant command, though I'm not sure what it means:

~$ apt-cache show libxml2|grep Version
Version: 2.6.32.dfsg-4ubuntu1.1
Version: 2.6.32.dfsg-4ubuntu1


Thank you very much for any help

Wiry

---

### Post by WiryLattice on 2009-03-16
I solved this by installing newer versions of both libxml2 and libxml2-dev from the lenny debian repository.

---

