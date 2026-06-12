---
title: "how to install promela/spin on ubuntu"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by se_landy on 2009-09-12
I need to install tool called spin (for verification of parallel algorithms). 

[here is the README file]("http://spinroot.com/spin/Man/README.html")

I never compiled anything on Ubuntu so I have no idea how install that. I've been trying for about half an hour now, but still no success... 
I follow directions from that file, unzipp it, do the "tar -xf" command, change directory to src, but when I try "make" command there is an error...

Help please :D

---

### Post by Partyboi2 on 2009-09-12
Hi, make sure you have installed the build-essential package first.
```
sudo apt-get install build-essential
```
Then run make again, if there are any errors post back what the errors are.

---

### Post by jvveiga on 2010-11-17
you need the bison package and the libc6-dev

[http://spinroot.com/spin/Bin/index.html](http://spinroot.com/spin/Bin/index.html) --> precompiled executables

---

