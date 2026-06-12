---
title: "HOWTO: compile kmymoney2"
date: 2005-11-30
forum: General Help
---

### Post by daller on 2005-11-30
*This howto is based on Breezy with KDE3.5 final*

This is how you compile kmymoney2-0.8.1

Download the source here:

[http://prdownloads.sourceforge.net/kmymoney2/kmymoney2-0.8.1.tar.bz2](http://prdownloads.sourceforge.net/kmymoney2/kmymoney2-0.8.1.tar.bz2)

Extract it, enter the folder, open a terminal and do this:

```
sudo apt-get install g++ libqt3-headers libqt3-mt-dev kdelibs4-dev libacl1-dev libattr1-dev

./configure

make

sudo make install
```

Now Kmymoney2 should be installed!

---

