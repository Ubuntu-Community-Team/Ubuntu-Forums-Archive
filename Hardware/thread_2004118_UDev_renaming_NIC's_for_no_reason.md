---
title: "UDev renaming NIC's for no reason"
date: 2012-06-15
forum: Hardware
---

### Post by headvampyre@hotmail.co.uk on 2012-06-15
I've recently encountered a problem after reinstalling ubuntu, where udev is renaming one of my NIC's. I've checked dmesg, and this is the output:

> root@PC1:/home/serveradmin# dmesg | grep udev
[    2.748661] udevd[118]: starting version 175
[    7.223897] udevd[356]: starting version 175
[    8.624289] udevd[379]: renamed network interface eth1 to eth2
[    9.328304] udevd[370]: renamed network interface eth0 to eth3

On top of this, when I attempt to use both of the devices when they've been renamed, the MAC address changes to the same as the other NIC (Happens to the PCI card and the builtin nic).

Would anybody have any solutions to this? I really need to get my NIC teaming working again.

---

