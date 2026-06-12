---
title: "Network interface - bridge problem"
date: 2008-11-24
forum: General Help
---

### Post by novice buntu on 2008-11-24
Hi,

I have 8.10 installed and a virtual machine configured. 

I followed the examples at [https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html#bridging](https://help.ubuntu.com/8.10/serverguide/C/network-configuration.html#bridging) 

to configure a bridge for the guest machine but now I am having routing problems with the host as well as the guest.

The symptoms are:

1) Every time I `/etc/init.d/networking restart` my resolv.conf file is emptied.

2) /etc/network/interfaces has a stanza for lo, eth0 and br0. I have given eth0 and br0 separate static addresses yet after restarting, ifconfig shows them as having the same address. 

3) I can ping from eth0 and br0 interfaces but , even after manually updating the resolv.conf, I am getting "Destination host unreachable" when I try and ping or traceroute out of my local subnet. I have the default gateway set correctly.


Can anyone offer any guidance? I am sure I am just configuring some things in the wrong place.

Thanx,
Dp.

---

### Post by novice buntu on 2008-11-24
This is fixed by the work-around at

[http://ubuntuforums.org/showthread.php?t=974382](http://ubuntuforums.org/showthread.php?t=974382)

---

