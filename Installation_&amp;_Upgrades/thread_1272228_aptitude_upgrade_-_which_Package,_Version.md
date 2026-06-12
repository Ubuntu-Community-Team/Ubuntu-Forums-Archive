---
title: "aptitude upgrade - which Package, Version"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2009-09-21
On Ubuntu 9.04

Before installing a package - How do I find out which version of that Package is available from aptitude?

---

### Post by stlsaint on 2009-09-22
depends on what you are installing...ie firefox you can go to site to see what version it is for...everything in the repos will be done via sudo apt-get update

---

### Post by ibuclaw on 2009-09-22
> **boondocks said:**
> On Ubuntu 9.04

Before installing a package - How do I find out which version of that Package is available from aptitude?

Do you mean the -V option?

ie:
```

$ [COLOR="Blue"]sudo aptitude -V dist-upgrade[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages will be upgraded:
  libneon27 [0.28.2-6.1 -> 0.28.2-6.1ubuntu0.1]  libneon27-gnutls [0.28.2-6.1 -> 0.28.2-6.1ubuntu0.1]  libpq5 [8.3.7-1 -> 8.3.8-0ubuntu9.04]  
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 558kB of archives. After unpacking 12.3kB will be used.
Do you want to continue? [Y/n/?]

```

Regards
Iain

---

### Post by boondocks on 2009-09-22
> **tinivole said:**
> Do you mean the -V option?

I mean, when I am searching for a package.  If found, which version is it?

```
 sudo    aptitude   search  Name_Of_Package
```

How do I make this tell me the version of the available package?

---

### Post by tommcd on 2009-09-22
> **boondocks said:**
> I mean, when I am searching for a package.  If found, which version is it?

```
 sudo    aptitude   search  Name_Of_Package
```

How do I make this tell me the version of the available package?
To see what version of a package you have installed and whether a newer version is available, or to see what version of a package you may want to install is offered in the repos, use **apt-cache policy** like this:
```

tom@ubuntu:~$ apt-cache policy firefox
firefox:
  Installed: 3.0.14+build2+nobinonly-0ubuntu0.9.04.1
  Candidate: 3.0.14+build2+nobinonly-0ubuntu0.9.04.1
  Version table:
 *** 3.0.14+build2+nobinonly-0ubuntu0.9.04.1 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
        100 /var/lib/dpkg/status
     3.0.8+nobinonly-0ubuntu3 0
        500 http://us.archive.ubuntu.com jaunty/main Packages

```
Note that apt-cache will tell you if a package is installed or not and what version is available in the repos.

---

### Post by boondocks on 2009-09-23
> **tommcd said:**
> To see what version of a package you have installed and whether a newer version is available, or to see what version of a package you may want to install is offered in the repos, use **apt-cache policy** like this:
```

tom@ubuntu:~$ apt-cache policy firefox
firefox:
  Installed: 3.0.14+build2+nobinonly-0ubuntu0.9.04.1
  Candidate: 3.0.14+build2+nobinonly-0ubuntu0.9.04.1
  Version table:
 *** 3.0.14+build2+nobinonly-0ubuntu0.9.04.1 0
        500 http://us.archive.ubuntu.com jaunty-updates/main Packages
        500 http://security.ubuntu.com jaunty-security/main Packages
        100 /var/lib/dpkg/status
     3.0.8+nobinonly-0ubuntu3 0
        500 http://us.archive.ubuntu.com jaunty/main Packages

```
Note that apt-cache will tell you if a package is installed or not and what version is available in the repos.

Thank you.
This is what I needed.

---

