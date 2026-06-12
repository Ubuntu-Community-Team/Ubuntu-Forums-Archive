---
title: "Resume with AMD AM3 processors"
date: 2014-10-10
forum: Hardware
---

### Post by Kim Foltz on 2014-10-10
There is a known bug with the AMD 10h processors that causes resume to fail. See [http://patchwork.ozlabs.org/patch/317774/](http://patchwork.ozlabs.org/patch/317774/) . This seems to include all of AMD's AM3 processors. Since there is a patch to fix the problem how do I tell when Ubuntu has applied the patch? I am currently using 64-bit Kubuntu 14.04 and resume from suspend doesn't work and would like to rule out this possibility.

---

### Post by Kim Foltz on 2014-10-11
If I understand things correctly this bug was fixed in Linux kernel 3.2.57-3+deb7u1, see [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746411](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746411) . The update to kernel 3.2.61 should fix this bug and seems to be in Kubuntu 12.04 but not 14.04. Is this really correct? If someone understands this I would appreciate an explanation.

---

