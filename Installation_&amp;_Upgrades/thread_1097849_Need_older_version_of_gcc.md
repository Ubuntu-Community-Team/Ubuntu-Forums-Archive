---
title: "Need older version of gcc"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by ajb2 on 2009-03-16
Hi,

This is my first posting to Ubuntu Forums...  apologies if I guessed the wrong forum to post to...

The Ubuntu I've installed has gcc version 4.3.2.  I need to install an earlier version (gcc 3.4) somewhere without replacing the 4.3.2 version that's there, so that I can create programs that run on other systems with older Linuxes.  I'd have to run the older version specially---that's OK; I don't want the older version to be the default.  I'm assuming something would have to be done to keep glibc libraries separate also.

Is there a fairly easy way to get this done from the repositories, or do I just need to go to the Gnu site and build this all by hand?

Thanks.

---

### Post by bapoumba on 2009-03-18
Moved to Installation & Upgrades.

From the repos, no, as the gcc version number is tied to the release you are using.
I have done it already, long ago, and do not remember how (I used a CC option before compiling).

I found this old link and think this is the way I did it:
[http://www.linuxforums.org/forum/installation/23695-installing-gcc-2-91-66-without-disturbing-existing-gcc-3-3-3-a.html](http://www.linuxforums.org/forum/installation/23695-installing-gcc-2-91-66-without-disturbing-existing-gcc-3-3-3-a.html)

---

### Post by mc4man on 2009-03-18
You can install *lower* versions from synaptic, in most cases with no issue.

The few times I need 3.4 I go 
CC=gcc-3.4 ./configure ...ect.,ect.

---

### Post by bapoumba on 2009-03-19
> **mc4man said:**
> You can install *lower* versions from synaptic, in most cases with no issue.

The few times I need 3.4 I go 
CC=gcc-3.4 ./configure ...ect.,ect.

I just looked, yes, and this is probably the way I did in my very first moments with Linux (had to compile that driver for my usb modem back then..). I'm running Hardy and installed gcc is 4.2.4. gcc 3.3 and 3.4 are available from synaptic.

Sorry for the misleading info. I quickly checked with aptitude, and it only showed the version I have installed.

---

### Post by ajb2 on 2009-03-20
Thanks---that worked great!  I guess I could have just tried this myself, but I didn't really know what it might screw up, so it was very helpful to hear from a more experienced user that there shouldn't be any issues.  Thanks again, mc4man & bapoumba.

---

