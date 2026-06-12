---
title: "named not starting after installing BIND 9.6.0-P1 on RHEL 4"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by satyendra on 2009-04-29
Hi all,

I have installed BIND 9.6.0-p1 on RHEL 4. Installation wen fine but while starting named (named -u named -g) it is giving error "Segmentation Fault".
Same error I am getting while generating rndc key too.

Tried solutions like creating /var/run/named directory with full permissions on the directory, tried renaming /lib/tcl to /lib/tcl.disable but bothing seems to be working.

Is it possible that I am using old LINUX Kernel version 2.6.9-22 which is creating the problem?

Also, Bind 9.5.0-P2 is working fine on the box.

-- Satyendra

---

