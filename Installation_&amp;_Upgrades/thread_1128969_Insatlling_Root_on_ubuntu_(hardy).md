---
title: "Insatlling Root on ubuntu (hardy)"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by Cenko on 2009-04-18
I'm triying to install programming language root on ubuntu 8.04. I got some problems. It tells me (I deleted the non-problematic lines)

```

Checking for X11/extensions/shape.h ... no
configure: X11/extensions/shape.h header (xorg-x11-proto-devel) MUST be installed
```
 
I have this package on my ubuntu. Even I tried to install it again. The package installer tells me:

```

cenk@Cenko:~/Desktop$ sudo dpkg -i xorg-x11-proto-devel_7.4-6_all.deb 
(Reading database ... 101363 files and directories currently installed.)
Unpacking xorg-x11-proto-devel (from xorg-x11-proto-devel_7.4-6_all.deb) ...
dpkg: error processing xorg-x11-proto-devel_7.4-6_all.deb (--install):
 trying to overwrite `/usr/include/X11/HPkeysym.h', which is also in package x11proto-core-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 xorg-x11-proto-devel_7.4-6_all.deb

```

Sometimes I get really tired. I install one package, it wants another one. Am I doing something wrong?

---

### Post by Brucevdk on 2009-04-18
> **Cenko said:**
> Am I doing something wrong?

Well, it would seem the common phrase "You're doing it wrong" would indeed apply here. Why don't you just use (instead of compiling from source):

```

sudo apt-get install root-system

```

Or even install it through Synaptic (System -> Administration -> Synaptic Package Manager).

---

### Post by Cenko on 2009-04-18
I tried it does not install that way. I found out that when I did ./configure it said "no" after checking some packages and files.But it did not stop process like before. How can i install these dependent on root?

I mean I want them to be deleted when I uninstall root.

---

### Post by Cenko on 2009-04-19
Ok! I did it finally!

You were right, I did it with apt-get. However before it was not able to find "root-system". After I made the change in the link, it worked. 



[http://mirror.phy.bnl.gov/debian-root/](http://mirror.phy.bnl.gov/debian-root/)

---

### Post by einsteiniixy on 2009-06-15
i did a search on the web for exactly the same problem (except my ubuntu is 9.04), and thanks to you guys.

---

### Post by Cenko on 2010-08-06
Well, now I use ubuntu 9.04 and installed root from root.cern.ch by dowloading the source. 

It's ofcourse easier by installing from apt-get, but then you won't have many features (At least it was so for me). It's better to install from source with options you want. It can keep asking you to install some packages, but be patient and install all these with aptitude. 

Then you'll have a better root than one in ubuntu repository.

---

