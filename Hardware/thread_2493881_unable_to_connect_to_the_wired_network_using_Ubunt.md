---
title: "unable to connect to the wired network using Ubuntu 22.04 for Raspberry Pi4"
date: 2023-12-28
forum: Hardware
---

### Post by sysongyi on 2023-12-28
I am unable to connect to the wired network using Ubuntu 22.04 for Raspberry Pi4, and the issue still persists after reinstalling Ubuntu 23.10 for Raspberry Pi4. Did I miss anything during installation?

---

### Post by sysongyi on 2023-12-28
The network is normal at the beginning of the system startup, but after 10 minutes without accessing the pi's IP address, it becomes inaccessible when the pi's IP address is accessed again.

---

### Post by TheFu on 2023-12-28
Don't know if this will help or not. I don't run Ubuntu on my Pi v4, but here's the network information, including driver and version.  Mine is setup to be 100% static on the Pi.  I don't use DHCP or wifi.  It has been working perfect without any issues at all for months, since I got it and setup OSMC onto it.

```
$ lshw -sanitize -C network
WARNING: you should run this program as super-user.
  *-network:0               
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: [REMOVED]
       size: 1Gbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=bcmgenet driverversion=5.15.92-1-osmc** duplex=full ip=[REMOVED] link=yes multicast=yes port=twisted pair speed=1Gbit/s
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmfmac driverversion=7.45.206 firmware=01-88ee44ea multicast=yes wireless=IEEE 802.11
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```
And the underlying release is:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Debian
Description:    Debian GNU/Linux 11 (bullseye)
Release:        11
Codename:       bullseye
```

---

