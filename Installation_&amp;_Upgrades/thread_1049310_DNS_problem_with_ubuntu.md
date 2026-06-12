---
title: "DNS problem with ubuntu"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by altaibskt on 2009-01-24
[FONT=Arial Black][SIZE=3][COLOR=Navy]Hi there!

please help me with my dns configuration, i am not good in linux and and i am so beginner, i made the dns configure mentioned in the tutorial but it didn't work at all,

now the problem that i missed with the dns files...

i need some hep to re-install the dns and reconfigure it i am so triad i spent to weeks trying to fixed and i googled it many mant time and did not find any good tutorials for beginners.

when i want to start the dns

Quote:
root@aaaa:~# /etc/init.d/bind9 restart
* Stopping domain name service... bind9
rndc: connect failed: 127.0.0.1#953: connection refused [fail]
* Starting domain name service... bind9 [fail]


my network interface is:

Quote:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
the output from
sudo vi /etc/hosts
is

Quote:
127.0.0.1 localhost server.localhost
172.17.207.33 iraqi-eng.homelinux.local server server01.local
theoutput from
sudo /etc/init.d/named start

Quote:
root@iraqi-eng:~# sudo /etc/init.d/named start
sudo: /etc/init.d/named: command not found
root@iraqi-eng:~#


pls i need help to reconfigure the dns and fix all my files...[/COLOR][/SIZE][/FONT]

---

### Post by altaibskt on 2009-01-24
up..:(

---

