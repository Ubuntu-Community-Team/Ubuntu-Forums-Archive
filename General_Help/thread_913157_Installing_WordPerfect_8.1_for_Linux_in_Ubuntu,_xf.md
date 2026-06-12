---
title: "Installing WordPerfect 8.1 for Linux in Ubuntu, xfree86"
date: 2008-09-07
forum: General Help
---

### Post by Pza3.14159 on 2008-09-07
I use WordPerfect for work and though I run a dual-boot and can run XP and WP Office X3 on that side, I would prefer to run Oo.org, and get WordPerfect for Linux running as well. I was fortunate? enough to find a boxed set of CorelLinuxOS at the thrift store, which includes the last (good) version of WordPerfect for Linux (8.1). Yes, I could just boot into XP, or maybe run X3 in Wine or VMware, but I want to try the native solution. WordPerfect is on the installation CD, in /dists/corellinux-1.0/corel/binary-i386/wp-full_8.1-12_i386.deb
I am running Hardy. I have read the WP for Linux FAQ and have yet to find a page addressing my problem:
When i attempt to install the package, I get the message:
Error: dependency is not satisfiable: xlib6g

Attempting to install xlib6g (also on the install CD), results in the following:
Error: dependency is not satisfiable: xfree86-common

xfree86-common in turn, can not be installed because it conflicts with x11-common.

So, the basic issue is that WP needs xfree86, but Ubuntu uses x11. Has anyone encountered this issue (either with WP or with another package depending on xfree86? Is it possible to get around this?

--bruce

---

### Post by john.nicholls on 2008-09-08
I had WordPerfect for Linux running many years ago, but it needed older versions of many libraries than are now available, so I eventually gave up on it. I doubt that you could get it working on Hardy.

---

### Post by 3rdalbum on 2008-09-08
A Debian package is actually an archive that contains three .tar.gz archives. If you use File Roller or ArK or something to open the package, and then decompress the "data.tar.gz" archive, you will find all the files and directories that the package installs.

If you manually drag those into the places where they need to be (it's all pretty self-explanatory - it's like a mini file system in there), theoretically you might be able to run WordPerfect. Just remember where all the files went in case you need to remove them later, and DO NOT allow them to overwrite any files that already exist in those directories!

---

