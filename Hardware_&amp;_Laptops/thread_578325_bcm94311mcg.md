---
title: "bcm94311mcg"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by jardo on 2007-10-17
hi to all
i just installed the release candidate of gutsy on my acer 5613zwlmi . as the title of the post i have that wireless card...i followed instructions in restricted driver manager to install firmware to make work the wireless card....and upgraded the system.
now i repeated this for two times...i mean after the first time i formatted and did it again..the reason is that i have problem with this card.
if i'm near the ap i get enough good connection,but as soon as i go a bit far away i can't connect...
if i type sudo iwlist scan i see the ap but i can't connect to it.
i tried to ping router and moving a bit distant from it...from1 meter to 5-6and this is the result:

 PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=150 time=2.49 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=150 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=150 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=150 time=2.35 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=150 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=150 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=150 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=150 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=150 time=2.35 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=150 time=5.69 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=150 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=150 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=150 time=2.37 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=150 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=150 time=2.39 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=150 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=150 time=2.36 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=150 time=25.2 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=150 time=4.94 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=150 time=4.07 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=150 time=2.47 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=150 time=2.35 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=150 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=150 time=2.35 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=150 time=2.35 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=150 time=2.37 ms
64 bytes from 192.168.1.1: icmp_seq=27 ttl=150 time=2.40 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=150 time=15.3 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=150 time=2.71 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=150 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=150 time=654 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=150 time=9.89 ms
64 bytes from 192.168.1.1: icmp_seq=33 ttl=150 time=70.7 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=150 time=565 ms
64 bytes from 192.168.1.1: icmp_seq=35 ttl=150 time=6.12 ms
64 bytes from 192.168.1.1: icmp_seq=36 ttl=150 time=75.9 ms
64 bytes from 192.168.1.1: icmp_seq=37 ttl=150 time=340 ms
64 bytes from 192.168.1.1: icmp_seq=38 ttl=150 time=937 ms
64 bytes from 192.168.1.1: icmp_seq=40 ttl=150 time=115 ms
64 bytes from 192.168.1.1: icmp_seq=44 ttl=150 time=193 ms
64 bytes from 192.168.1.1: icmp_seq=45 ttl=150 time=266 ms
64 bytes from 192.168.1.1: icmp_seq=50 ttl=150 time=1165 ms
64 bytes from 192.168.1.1: icmp_seq=54 ttl=150 time=40.8 ms
From 192.168.1.80 icmp_seq=101 Destination Host Unreachable

hope someone could help me...
thanks to everyone for reading

---

### Post by jardo on 2007-10-17
possible that i'm the only having this problem? :( noone has idea of what could be the problem?

---

