---
title: "Installation error with Nmap 5.003"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by dpau on 2009-10-14
Hi everyone,

i am new to linux and ubuntu and I got an error: dependency is not satisfiable: libcap0.8 when i am trying to install nmap_5.00-3_i386.deb on my machine.  Anyone got any advice what I should do next?  thanks

---

### Post by dpau on 2009-10-14
When i try to dpkg -i at command line, it gave me error below:
david@themachine:~/Desktop$ sudo dpkg -i nmap_5.00-3_i386.deb
(Reading database ... 137101 files and directories currently installed.)
Preparing to replace nmap 5.00-3 (using nmap_5.00-3_i386.deb) ...
Unpacking replacement nmap ...
dpkg: dependency problems prevent configuration of nmap:
 nmap depends on libpcap0.8 (>= 1.0.0-1); however:
  Version of libpcap0.8 on system is 0.9.8-2.
 nmap depends on libpcre3 (>= 7.7); however:
  Version of libpcre3 on system is 7.4-1ubuntu2.1.
dpkg: error processing nmap (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nmap
david@themachine:~/Desktop$ 

I also force install libpcap0.8 & libpcre3 and I still got the same error

---

