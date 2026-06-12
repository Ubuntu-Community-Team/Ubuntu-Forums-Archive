---
title: "Wireless vs Wired on Lenovo 3000 C100"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by darrenm on 2007-02-02
Hello all.

I'm running wifi off the broadcom 4319 fine using the open driver and the firmware from bc43xx-fwcutter.

I use the ethernet cable when sitting at my desk and wifi when not. My ethernet adapter is eth0 and the wifi is eth1

If I plug the ethernet cable in I don't get any network until I do ```
sudo ifdown eth1
``` then it removes the route from the routing table and my network/internet works fine through the ethernet cable. Also if I want to use the wifi I have to do ```
sudo ifdown eth0
```

I'm sure its because the routing table is identical for both entries:
```
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
```
Therefore it can't decide the best route to take. Perhaps I need to up the metric on eth1 so it will take eth0 if its available?

I use NetworkManager but can't think why I would need it at the moment.

Any ideas? 
Thanks

---

### Post by darrenm on 2007-02-03
Anyone? I just need to force one interface to have precedence over the other.

---

