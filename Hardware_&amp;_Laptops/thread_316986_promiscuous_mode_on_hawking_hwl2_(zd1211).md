---
title: "promiscuous mode on hawking hwl2 (zd1211)"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by Ryanmt on 2006-12-11
Having trouble getting wireshark working on ubuntu, it picks up my own packets but not other ones. i have the promiscus tab ticked too.

ive tried

ryanmt@penguin:~/Desktop$ sudo ifconfig wlan0 -promisc
but i just end up back at the prompt

dmesg is full of so i cant see if its done anything.
[17183172.736000] zd1211:zd1205: cmd = 8b27
[17183173.736000] zd1211:zd1205: cmd = 8b03
[17183173.736000] zd1211:zd1205: cmd = 8b09
[17183173.736000] zd1211:zd1205: cmd = 8b1d
[17183173.736000] zd1211:zd1205: cmd = 8b27

ive tried two versions of the driver
zd1211-driver-r77 and r83 both have the same thing (the later version doesnt full up dmesg though)

when i run airoscript i get this error too

ryanmt@penguin:~/Desktop$ ./airoscript-1.7RC7.sh 
./airoscript-1.7RC7.sh: 35: function: not found
SIOCSIFFLAGS: Permission denied

wlan0 ZyDAS zd1211 (monitor mode enabled)
./airoscript-1.7RC7.sh: 39: Syntax error: "}" unexpected

---

### Post by Ryanmt on 2006-12-12
bump :(

---

### Post by cmavr8 on 2008-05-14
Me too, any updates?

---

