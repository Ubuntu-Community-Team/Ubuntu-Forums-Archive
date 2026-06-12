---
title: "Ubuntu server + iSCSI = failling network"
date: 2011-07-12
forum: Hardware
---

### Post by zee on 2011-07-12
Hi.
  I have set up a server, that will server as the main fileserver in our group. This server has two ethernet cards, one is connected to our network, the other goes to an Infortrend NAS via iSCSI.

  The network interfaces are configured as follows:
```
# The primary network interface
auto eth0
iface eth0 inet static
  address 192.168.65.2
  netmask 255.255.255.0
  gateway 192.168.65.1
  dns-nameservers 192.168.60.5 193.2.1.66 193.2.1.72 8.8.8.8
  dns-search ki.si

# iSCSI connection
auto eth1
iface eth1 inet static
  address 10.0.0.1
  netmask 255.255.255.0
  gateway 192.168.65.2
  dns-nameservers 192.168.60.5 193.2.1.66 193.2.1.72 8.8.8.8
  mtu 6500
```

  The NAS is seen by the server as a huge 20 TB hard drive, partitioned into one partition, formated to XFS.

  Problem is that every once in a while this iSCSI connection appears to fail. Could it be something wrong with the configuration on the server/NAS ? If so, where could I like for errors.

Best regards,
zee

---

