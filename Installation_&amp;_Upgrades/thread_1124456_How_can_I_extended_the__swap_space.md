---
title: "How can I extended the  swap space ?"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-04-13
I am trying to install oracle oracle-xe-universal_10.2.0.1-1.0_i386.deb.
I am getting the following errors
------------------------------------------------------------------------
luc@ubuntu:~/Desktop$ sudo dpkg -i --force-architecture oracle-xe-universal_10.2.0.1-1.0_i386.debdpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package oracle-xe-universal.
(Reading database ... 144107 files and directories currently installed.)
Unpacking oracle-xe-universal (from oracle-xe-universal_10.2.0.1-1.0_i386.deb) ...
This system does not meet the minimum requirements for swap space.  Based on 
the amount of physical memory available on the system, Oracle Database 10g 
Express Edition requires 1024 MB of swap space. This system has 948 MB 
of swap space.  Configure more swap space on the system and retry the installation.
dpkg: dependency problems prevent configuration of oracle-xe-universal:
 oracle-xe-universal depends on libaio (>= 0.3.96) | libaio1 (>= 0.3.96); however:
  Package libaio is not installed.
  Package libaio1 is not installed.
dpkg: error processing oracle-xe-universal (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 oracle-xe-universal
luc@ubuntu:~/Desktop$

---

### Post by NoReflex on 2009-04-13
You can find detailed information about swap usage in Ubuntu here : 
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Best wishes,
NoReflex

---

