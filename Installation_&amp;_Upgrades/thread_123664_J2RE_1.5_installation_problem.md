---
title: "J2RE 1.5 installation problem"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by hell0un1verse on 2006-01-30
Hi there,

I installed sun-j2re1.5 package via apt-get install, but when I tried java -version after installation, the command returned with following:

[B]java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.[/B]

It seems that the J2RE1.5 has been installed, but not really takes effect. Do I need to do some post-install configuration to have it run? Thanks for your help.

---

### Post by kaamos on 2006-01-30
Try this:
```
sudo update-alternatives --config java
```

[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

---

### Post by hell0un1verse on 2006-01-30
Thanks a lot! Problem solved:)

---

