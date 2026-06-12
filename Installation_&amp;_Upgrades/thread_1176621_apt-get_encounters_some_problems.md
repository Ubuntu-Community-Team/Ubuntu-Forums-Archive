---
title: "apt-get encounters some problems"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by merciadriluca on 2009-06-02
Hello,

I firstly wanted to install BOINC package for Ubuntu. Anyway, it seemed not to work properly (I never received data paquets: in the Messages tab, it was always displaying that I had 0 Mb free; anyway, the BOINC options and root directory were correctly given). In fact, it was the 6.xx version (called "pre-release"), which seems to be a little (only?) buggy. I figured it out when I saw that the version I was running on a Debian machine was a 5.xx, which was working correctly.

Btw, I wanted to uninstall it, using apt-get remove. Meanwhile, I installed another version, which figured out to be a 6.xx too (that I had to remove too). This version was a .tar.gz containing some scripts to install it. Anyway, the installation script of this tarball wanted me to upgrade m4 and autoconf. I wanted, but it failed. I reported the bug at [https://bugs.launchpad.net/ubuntu/+source/m4/+bug/382790]("https://bugs.launchpad.net/ubuntu/+source/m4/+bug/382790") (the smartcard problem is another one). 

I now have a good package containing a former version of BOINC, but it does not want to uninstall. It is due to the fact that I have to ``repair'' m4 and autoconf. That's what I tried, but when I try to uninstall m4, I have
```

$ sudo apt-get remove m4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  m4
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 553kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing m4 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 m4
E: Sub-process /usr/bin/dpkg returned an error code (1)

```.

What can I do?

Thanks.

---

### Post by cariboo on 2009-06-02
Go to System-->Administratiion-->Synaptic Package Manager-->Edit-->Fix Broken Packages, and repair the problem package.

---

### Post by merciadriluca on 2009-06-02
It evidently said it has successfuly be done, but the result is the same when I type
```
sudo apt-get remove m4
```.:(

---

