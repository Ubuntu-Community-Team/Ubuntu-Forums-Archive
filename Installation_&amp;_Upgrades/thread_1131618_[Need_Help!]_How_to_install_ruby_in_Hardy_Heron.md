---
title: "[Need Help!] How to install ruby in Hardy Heron???"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by GuyFreakz on 2009-04-21
Hi, guyz!

I tried to install ruby in my linux ubuntu 8.04.1 LTS: 
> sudo apt-get install ruby
then this message out:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ruby


After that i tried this:
> sudo apt-get install ruby1.8
and this message out:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libruby1.8
Suggested packages:
  rdoc1.8 ri1.8 ruby1.8-examples
The following NEW packages will be installed:
  libruby1.8 ruby1.8
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 1408kB of archives.
After this operation, 5890kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libruby1.8 1.8.6.111-2ubuntu1.1
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main ruby1.8 1.8.6.111-2ubuntu1.1
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.6.111-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.6.111-2ubuntu1.1_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/ruby1.8_1.8.6.111-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/ruby1.8_1.8.6.111-2ubuntu1.1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


How can these happen, and how can i install ruby? i want to study ruby asap. Plz help. Thx!!!

---

### Post by Partyboi2 on 2009-04-21
Try reloading the package list first before trying to install, so open a terminal (Application>Accessories>terminal) and
```
sudo apt-get update
sudo apt-get install ruby1.8
```

---

### Post by GuyFreakz on 2009-04-21
> **Partyboi2 said:**
> Try reloading the package list first before trying to install, so open a terminal (Application>Accessories>terminal) and
```
sudo apt-get update
sudo apt-get install ruby1.8
```

Hey, it's work!! Thanks buddy ;)

---

