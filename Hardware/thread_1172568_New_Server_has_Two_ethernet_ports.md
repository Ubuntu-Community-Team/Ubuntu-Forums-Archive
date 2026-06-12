---
title: "New Server has Two ethernet ports"
date: 2009-05-28
forum: Hardware
---

### Post by R.Bucky on 2009-05-28
I just received my new web server yesterday. I noticed that it has dual ethernet ports. From what I can tell, one can be used for connection to the internet and the other for say an internal LAN. Has anyone configured Ubuntu Server for duplexing? Or, is that the correct term? In other words, is it possible to increase broadcast efficiency from my server by using both ports.

Experiences?

---

### Post by pytheas22 on 2009-05-28
My server has two NICs as well.  One is assigned a public IP address and is used for normal connections to the outside world.  The other is attached to the local SAN, which runs on its own private network.  I think this is the most typical use for a second NIC.

If you want to use both NICs to connect to the outside world, thereby increasing your bandwidth, this [how-to]("http://www.howtoforge.com/network_bonding_ubuntu_6.10") might be useful, although it's a bit old.  Of course, keep in mind that bonding the interfaces will only increase bandwidth if the greatest bottleneck in your connection to the outside world is the maximum transfer speed of the NIC--in other words, if your NIC is capable of 100 gigabytes/second but your link to the Internet is only 10 gigabytes/second, bonding the NICs isn't going to help.

---

### Post by R.Bucky on 2009-05-29
Thanks for the explanation. That explains it. My NIC is not the bottleneck. I might try using it for my intranet. 

Mark

---

### Post by laercio on 2009-06-13
I've been trying to bond 2 NIC cards without success!
Every howto refers to configuration files and commands (like update-modules) that are no longer present in Ubuntu 9.04 server.

Does anybody know the new procedures for the right configuration?

Regards,

Laércio

---

