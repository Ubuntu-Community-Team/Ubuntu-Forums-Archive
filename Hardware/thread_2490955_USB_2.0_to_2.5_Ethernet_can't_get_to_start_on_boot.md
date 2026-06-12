---
title: "USB 2.0 to 2.5 Ethernet can't get to start on boot."
date: 2023-09-21
forum: Hardware
---

### Post by Raymond Day on 2023-09-21
I been working on this all morning and rebooted like 10 times.

It has a built in Gigabit Ethernet but I want it to not use that and use the USB 3.0 to 2.5 Ethernet adaptor I have plug in it's USB 3.0 port.

This my help to help me the command line it's only a server no desktop.

```
root@comqi-rp507:~# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 90:e2:fc:b1:39:8d brd ff:ff:ff:ff:ff:ff
    inet 192.168.86.87/24 brd 192.168.86.255 scope global dynamic enp3s0
       valid_lft 85532sec preferred_lft 85532sec
3: enx00e04c680050: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:e0:4c:68:00:50 brd ff:ff:ff:ff:ff:ff
    inet 192.168.86.86/24 brd 192.168.86.255 scope global dynamic noprefixroute enx00e04c680050
       valid_lft 84945sec preferred_lft 84945sec
    inet6 fe80::ea6d:9314:5596:489a/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
4: wlp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 80:19:34:65:a0:63 brd ff:ff:ff:ff:ff:ff
root@comqi-rp507:~# netplan apply
/etc/netplan/00-installer-config.yaml:4:1: Invalid YAML: tabs are not allowed for indent:
         enx00e04c680050:
^
root@comqi-rp507:~#
```

I had to hook a screen and keyboard to it so it got a IP. Just did:

dhclient enp3s0 and it got a IP.

I did the same with the 2.5 ethernet like this:

```
dhclient enx00e04c680050
RTNETLINK answers: File Exists
```

I made a new file at /etc/netplan/99_config.yaml

In it looks like this:

```
network:
  version: 2
  renderer: networkd
  ethernets:
  enx00e04c680050:
      dhcp4: true
```

But when I do netplan apply it gives me the error you can see in the last of the 1st code in here.

I looked on bing and google for help and after about 6 hours came here.

Could about reload it but that would take days.

Thank you.

-Raymond Day

---

### Post by Raymond Day on 2023-09-21
Got it working. I deleted the **00-installer-config.yaml** and in the **99_config.yaml I put this:**

network:
  version: 2
  renderer: networkd
  ethernets:
    enx00e04c680050:
      dhcp4: true
      dhcp6: true

Rebooted and now it get's a IP.

-Raymond Day

---

