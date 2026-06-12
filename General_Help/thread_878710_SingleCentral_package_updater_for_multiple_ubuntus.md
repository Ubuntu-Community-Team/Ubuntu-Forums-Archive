---
title: "Single/Central package updater for multiple ubuntus"
date: 2008-08-03
forum: General Help
---

### Post by ProfessionalNewbie on 2008-08-03
Hi all,

I wasn't able to find this in a previous post but is there a way to have a single computer run apt-get update & all other computers point to this one computer to get its package updates?
I have a few computers at home all running various flavours of ubuntu & just want 1 to do the package downloads & have the others point to this computer for the package updates instead of all downloading separately.
I've heard that RHEL have this feature via RHN & wanted to know what similar feature is available for Ubuntu.
Thanks in advance.

pn.

---

### Post by Elfy on 2008-08-03
I think you are looking for apt-proxy

> Because apt-proxy behaves as if it were a HTTP server with a full copy of the repositories you select, you can access the packages from other computers on your network.

[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)

[http://apt-proxy.sourceforge.net/](http://apt-proxy.sourceforge.net/)

---

