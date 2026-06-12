---
title: "More of my Package Problems!"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by Ratscallion on 2009-03-31
Yet again, I have plenty of package problems under my belt. This time, I can't seem to solve them using either of these two:
```
sudo dpkg --configure -a
```and
```
sudo apt-get install -f
```When I try the latter version of that, I get the following error:
>  E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/liblcms1_1.16-10ubuntu0.2_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptor
dpkg-deb: `/var/cache/apt/archives/liblcms1_1.16-10ubuntu0.2_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/liblcms1_1.16-10ubuntu0.2_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/liblcms1_1.16-10ubuntu0.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
When I do an apt-get update I don't even get an error!
I don't see why any of this is happening, and have also made an attempt to re-install the packages mentioned in the first error.
Please help me as I need to install a few packages and run some updates and wish to do so without these errors.
Thanks for all the help in advance!

---

### Post by Partyboi2 on 2009-04-01
Have you tried to empty the cache before reinstalling the package?
```
sudo apt-get clean
sudo apt-get --reinstall install liblcms1
```

---

