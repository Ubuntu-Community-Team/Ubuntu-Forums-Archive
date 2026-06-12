---
title: "Ubuntu 8.10 Server amd64 &amp; iscsi=true"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by Kermee on 2009-03-27
Hi All-

I'm having a heck of a time installing Ubuntu 8.10 Server amd64 to an iSCSI target during installation.  I'm using ubuntu-8.10-server-amd64.iso as the install media.

As documented, passing "iscsi=true" to the kernel (via F6) during setup should bring up the configuration screen of adding an iSCSI target. However, it never comes up.

Does anyone have any idea on how to install Ubuntu 8.10 Server to an iSCSI target during installation?  It's so easy under RHEL, CentOS & Fedora Core...

Thanks in advance!

Cheers,
Kermee

---

### Post by blopeur` on 2009-04-16
Their is a missing file ( actually link ). 

It can be easily fixed, when your install has reach the iscsi config step, switch to console and do ln -s /sbin/iscsi-iname /usr/sbin/iscsi-iname


Then just get back to the installer and enter the target ip and voila !

---

