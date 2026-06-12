---
title: "VMware and Ubuntu"
date: 2008-08-20
forum: General Help
---

### Post by esullivan on 2008-08-20
We have a Ubuntu box with an internal website on it.  We recently got a server for VMware and I was hoping to IMPORT the Ubuntu box into a virtual server.

When I try and import I get " Unable to connect to the remote VMware Converter Agent - host may be down or firewalled"

I do not believe there is a software firewall on the box and the machine is powered on.

I have done some searching and found that vm does not support a Linux import, but that some people have found ways around this.

Anyone know a Linux product that will help?

---

### Post by LUS93 on 2008-08-20
* Install Ubuntu into a VMWare instance.
* Log into the existing webserver and tar up the website (including apache configs, as necessary).
* Log into the VM, copy the tarball over, extract it and start Apache.

Moving a Linux install to VMWare is a LOT less involved than Windows. If all else fails, dump/restore the box into the VM.

---

### Post by esullivan on 2008-08-20
Thanks!

---

