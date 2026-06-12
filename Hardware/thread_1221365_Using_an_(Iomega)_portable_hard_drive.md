---
title: "Using an (Iomega) portable hard drive"
date: 2009-07-23
forum: Hardware
---

### Post by talon12311 on 2009-07-23
Hey,

I have an Iomega Prestige portable hard drive and would like to know how to make it work with Ubuntu.  I've cruised around the forums a bit and haven't been able to find a good guide.  I noticed that 'dmesg' is a common tool used as a first step in figuring these things out so I ran 'dmesg | tail -n10' after plugging in my hard drive and got the following output:

> 
[   13.745718] type=1505 audit(1248389733.940:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2114
[   13.831660] type=1505 audit(1248389734.024:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2119
[   13.831788] type=1505 audit(1248389734.024:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2119
[   13.851942] type=1505 audit(1248389734.044:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2123
[   17.186091] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.186093] Bluetooth: BNEP filters: protocol multicast
[   17.262048] Bridge firewalling registered
[   18.681932] ppdev: user-space parallel port driver
[   22.811068] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.028075] eth1: no IPv6 routers present
Any thoughts?

Thanks,

talon

---

