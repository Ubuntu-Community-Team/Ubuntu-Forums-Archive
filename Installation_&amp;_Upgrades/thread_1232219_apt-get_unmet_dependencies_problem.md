---
title: "apt-get unmet dependencies problem"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by avilanchee on 2009-08-05
I installed sqlite3 . this the problem i get when i install the dev library which the sqlite3-ruby gem needs. Any heelp would be highly appreciated


avinash@SKYLINE:~$ sudo apt-get install libsqlite3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsqlite3-dev: Depends: libsqlite3-0 (= 3.6.10-1) but 3.6.10-1ubuntu0.2 is to be installed
E: Broken packages

---

