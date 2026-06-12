---
title: "How to download &amp; install g++ in Ubuntu 9.04?"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by sreejithbabu on 2009-07-16
I have downloaded  *g++-3.4_3.4.6-1ubuntu2_i386.deb*  &  *g++_4.3.3-1ubuntu1_i386.deb* from the net.
When I doubled clicked this in Ubuntu, and selected install package they are showing errors like 
   [B]Error: Dependency is not satisfiable: gcc-3.4-base (= 3.4.6-1ubuntu2)
   Error: Dependency is not satisfiable: g++-4.3 (>= 4.3.3-1)[/B]
for each of them respectively.
Are these downloaded packages correct or did I use the wrong way to install them?
I want to know how install g++ in Ubuntu.

---

### Post by csabo2 on 2009-07-16
use apt to install it. its telling you exactly whats missing.  if you use the built in package manager, it will download thoes dependencies for you.

---

### Post by johndoe32102002 on 2009-07-16
In terminal, type:
sudo apt-get install build-essential

This will install g++ in Ubuntu 9.04 (and other versions of Ubuntu and Debian).

---

