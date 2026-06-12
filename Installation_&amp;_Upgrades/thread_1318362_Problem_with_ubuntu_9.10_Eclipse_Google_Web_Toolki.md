---
title: "Problem with ubuntu 9.10 Eclipse Google Web Toolkit Xulrunner"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by breidert on 2009-11-07
Hi everyone,

after upgrading to ubuntu 9.10 my manually installed eclipse does not start up the preview browser of google web toolkit (GWT) any more.

The error is

/usr/lib/jvm/java-6-openjdk/bin/java: symbol lookup error: /usr/lib/xulrunner-1.9.1.4/libxul.so: undefined symbol: PR_GetPhysicalMemorySize

This happens both with Eclipse 3.4 and 3.5, i tested both.

The error tells me nothing, googling also does not bring anything that makes sense to me. If anybody has an idea or hint it would be appreciated, I have spent too much time and headbanging on this.

I think it has something to do with firefox !?!

With ubuntu 9.04 and eclipse3.4 it worked fine. In ubuntu 9.04 the firefox version was 3.0. Now with ubuntu 9.10 the firefox version is 3.5.

Cheers and thx, Christoph

---

### Post by breidert on 2009-11-15
I fixed the problem by changing to Sun's JDK in eclipse's project
settings

Instead of /usr/lib/jvm/java-6-openjdk
I now use /usf/lib/jvm/java-6-sun-1.6.0.16

Now everything work's nice and smoothly just like before I upgraded
Ubuntu.

Cheers,

Christoph

---

