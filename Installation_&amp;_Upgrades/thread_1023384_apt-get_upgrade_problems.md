---
title: "apt-get upgrade problems?"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by putz3000 on 2008-12-27
I am running 8.04.1 server edition and when I run sudo apt-get upgrade (after first running sudo apt-get update), there are 7 "packages" kept back.  I am  not sure why, or if it is ok.  Maybe I need to do something to my source list?  Here are the results I get:

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libisccc30 libisccfg30 linux-image-server
  linux-server
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
magicman@Evo:~$

Any idea's about what is going on or if I need to be concerened?

thanks

---

### Post by gettinoriginal on 2008-12-27
You did update, then upgrade, you should probably do another update.

---

### Post by putz3000 on 2008-12-27
does not matter how many times I do an update, this has been going on now for some time.  

Is it possible that these 7 packages are somehow connected to a problem with webmen?  I installed webmen and at the time had to go to debians source and everything was all right at the time, but now it errors over the source location as well.  I have just been too lazy to fix it - server is not Internet facing.

---

### Post by Partyboi2 on 2008-12-27
Have you tried 
```
sudo apt-get dist-upgrade
```

---

### Post by putz3000 on 2009-01-01
Yes, that did the trick (apt-get dist-upgrade).  What is the main differance between apt-get upgrade and apt-get dist-upgrade?

---

### Post by Partyboi2 on 2009-01-01
> **putz3000 said:**
> Yes, that did the trick (apt-get dist-upgrade).  What is the main differance between apt-get upgrade and apt-get dist-upgrade?
  Taken from apt-get manpage
>  upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.

---

