---
title: "VMware Arrow Keys Issue"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by Daveyon on 2009-03-18
Ok, Iv installed VMware 6.5.1 on my system. Loaded up xp or win server 2003, the up, dwn, left & right keys wont work. Any experience with what I face u guys wanna share?

Those keys work in the guest OS but.

---

### Post by Hercynium on 2009-05-15
I had this same issue, and found the fix here:

[http://linuxsysconfig.com/2009/03/vmware-arrow-keys-issues/](http://linuxsysconfig.com/2009/03/vmware-arrow-keys-issues/)

Simply add the following line to /etc/vmware/config

xkeymap.nokeycodeMap=true

---

