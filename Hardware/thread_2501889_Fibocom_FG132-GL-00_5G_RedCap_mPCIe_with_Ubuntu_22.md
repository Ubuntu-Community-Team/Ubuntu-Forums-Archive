---
title: "Fibocom FG132-GL-00 5G RedCap mPCIe with Ubuntu 22.04"
date: 2024-10-24
forum: Hardware
---

### Post by morta1985 on 2024-10-24
Hi!

I have a LX2162a ARM Board and on it a Fibocom FG132-GL-00 5G RedCap mPCIe Card for WWAN.

It found with lsusb but not with mmcli, ip a or /dev/tty. Why?

lsusb

```
root@LX2162a:~# lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 2cb7:0112 Fibocom Fibocom Module
Bus 001 Device 002: ID 0424:2514 Microchip Technology, Inc. (formerly SMSC) USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

root@LX2162a:~# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: dummy0: <BROADCAST,NOARP> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether e2:62:a4:aa:f6:46 brd ff:ff:ff:ff:ff:ff
3: sit0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN group default qlen 1000
    link/sit 0.0.0.0 brd 0.0.0.0
4: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 56:c9:3b:9b:f3:e1 brd ff:ff:ff:ff:ff:ff
5: eth1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 62:44:42:aa:a0:23 brd ff:ff:ff:ff:ff:ff
6: eth2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 6e:26:7f:85:84:b9 brd ff:ff:ff:ff:ff:ff
7: eth3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 92:74:83:a4:91:9c brd ff:ff:ff:ff:ff:ff
8: eth4: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 6e:e5:de:ec:2e:a9 brd ff:ff:ff:ff:ff:ff
9: eth5: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 36:f6:fe:06:1a:37 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.215/24 brd 192.168.1.255 scope global dynamic eth5
       valid_lft 5483sec preferred_lft 5483sec
    inet6 2a02:168:a774::cd3a/128 scope global
       valid_lft forever preferred_lft forever
    inet6 fe80::34f6:feff:fe06:1a37/64 scope link
       valid_lft forever preferred_lft forever
10: eth6: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether de:a4:9f:bf:ab:a7 brd ff:ff:ff:ff:ff:ff
11: eth7: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 9a:71:b6:57:46:48 brd ff:ff:ff:ff:ff:ff
12: eth8: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 42:d5:c6:25:a8:5a brd ff:ff:ff:ff:ff:ff
13: eth9: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 26:02:4d:9b:bc:be brd ff:ff:ff:ff:ff:ff
14: eth10: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 1a:dc:14:a2:4f:2f brd ff:ff:ff:ff:ff:ff
15: eth11: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 06:9f:63:bd:32:a7 brd ff:ff:ff:ff:ff:ff

```



dmesg [https://pastebin.com/UTLUGMth](https://pastebin.com/UTLUGMth)

---

