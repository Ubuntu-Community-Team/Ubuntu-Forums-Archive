---
title: "Firewire Connection"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by jck3j on 2007-01-10
Does anyone know of a good way to connect two computers using firewire to access the other computer's hard drives? i know you can do it on xp (ew) via a network connection, but i haven't figured out to set up a network connection on ubuntu.

---

### Post by RandomJoe on 2007-01-11
You can do Ethernet over Firewire using the 'eth1394' module.  I've never used it, I think it requires a special cable?  Or maybe just a 4-pin FW cable so you don't connect power?  A quick Google search doesn't turn up much info - I did find this:

[http://www.linux1394.org/eth1394.php](http://www.linux1394.org/eth1394.php)

Which says it isn't stable...!

It appears on loading the module another ethX will appear, and you configure it just like any other.

---

