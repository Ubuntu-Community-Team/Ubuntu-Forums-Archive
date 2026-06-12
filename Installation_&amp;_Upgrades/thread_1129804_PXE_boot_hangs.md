---
title: "PXE boot hangs"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Arsen.Shnurkov on 2009-04-19
I follow this guide
[https://wiki.ubuntu.com/LiveCDNetboot](https://wiki.ubuntu.com/LiveCDNetboot)

After loading vmlinux and initrd.gz system hangs with messages:

...
[    4.854139] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.960401] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow control: RX/TX
[   17.960788] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   36.320991] RPC: Registering udp transport module
[   36.321055] RPC: Registering tcp transport module

eth0 is an wired adapter connected to DLINK gigbit switch
kubuntu is from 
[http://mirror.yandex.ru/ubuntu-releases/kubuntu/9.04/kubuntu-9.04-rc-desktop-i386.iso](http://mirror.yandex.ru/ubuntu-releases/kubuntu/9.04/kubuntu-9.04-rc-desktop-i386.iso)

What I need to do to boot?

---

