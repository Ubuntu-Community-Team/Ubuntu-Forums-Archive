---
title: "Please help package manager broken on fresh install"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by Arrowx7 on 2009-07-28
Running hardy server on amd64
$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done

$ sudo apt-get install mysql-client-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mysql-client-5.0: Depends: libdbd-mysql-perl (>= 1.2202) but it is not installable
                    Depends: libdbi-perl but it is not installable
E: Broken packages


I try install libdbd-mysql-perl manually using apt-get libplrpc-perl and it fails, everything fails (even apt-get install nmap), nothing installs.  The package manager is broken.

Please help

---

### Post by Partyboi2 on 2009-07-28
Hi, open up Software Sources (System>Admin>Software Sources) an under the first tab make sure you have all the repos enabled except source code and 'installable from cd/dvd'. Then move to the "updates" tab and make sure the first two are enabled. Then reload the package list and try installing 'mysql-client-5.0'.

---

