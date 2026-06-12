---
title: "compaq v2000 wireless not working"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by youbaji on 2007-07-08
Hello all,
I have a compaq v2000 laptop with:
AMD Turon64
Broadcom 4318 network adaptor
Ubutun 7.04 Feisty


My problem is that I cannot connect to internet.

It seems like that the network adaptor has been recoganized, but has not been turned on.

There is a "wireless button" which works in windows but no in linux.

**xi@xi:~$ sudo ifup eth1**
SIOCSIFFLAGS: No such file or directory
There is already a pid file /var/run/dhclient.eth1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:14:a5:11:98:a6
Sending on   LPF/eth1/00:14:a5:11:98:a6
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
receive_packet failed on eth1: Network is down


**xi@xi:~$ cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


I tried solution from here: [http://ubuntuforums.org/showthread.php?p=2893638](http://ubuntuforums.org/showthread.php?p=2893638)
but no luck.


I triedd another laptop Dell inspiron 6000 with
Intel 2200BG
and it works fine.

Any suggestions?

Thanks!

---

