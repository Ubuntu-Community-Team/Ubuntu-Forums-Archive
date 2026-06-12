---
title: "ubuntu server"
date: 2008-11-24
forum: General Help
---

### Post by hirohitosan on 2008-11-24
Hi there.

I just installed ubuntu server edition.
My computers has a real IP. How can I set the IP, DNS, Gateway, Netmasc?

How can I update the server edition?

Thanks

---

### Post by geirha on 2008-11-24
The Ubuntu Server Guide covers these things.

Ubuntu 8.04 Hardy Heron [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

Ubuntu 8.10 Intrepid Ibex [https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)

---

### Post by Walter_Crankite on 2008-11-24
I don't see how an IP address can be unreal?
Just go to /etc/network/interfaces and change the config.

auto ethx
iface ethx inet static
     address x.x.x.x
     network x.x.x.x
     netmask x.x.x.x
     broadcast x.x.x.x
     gateway x.x.x.x

After this restart the networking service:
/etc/init.d/network restart


Walter

---

### Post by hirohitosan on 2008-11-24
I want to install a ftp server also. Do you have any sugestions?

Thanks!

---

