---
title: "create a tunnel between client and server"
date: 2008-10-19
forum: General Help
---

### Post by mmbathan on 2008-10-19
Hi all,

I try to create a tunnel between client and server I used this command to create the tunnel

server : 
```
ip tunnel add tun0 mode ipip remote 10.1.1.2 local 10.1.1.1 dev eth1
ifconfig tun0 10.1.1.1 netmask 255.255.255.252 pointopoint 10.1.1.2
ifconfig tun0 mtu 1500 up

```

client:
```
ip tunnel add tun1 mode ipip remote 10.1.1.1 local 10.1.1.2 dev eth4
ifconfig tun1 10.1.1.2 netmask 255.255.255.252 pointopoint 10.1.1.1
ifconfig tun1 mtu 1500 up

```

but I am still could not ping each other while I can ping without tunneling.

```
bagside@bagvapp:~$ ping 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
From 10.1.1.2 icmp_seq=2 Destination Host Unreachable
From 10.1.1.2 icmp_seq=3 Destination Host Unreachable
From 10.1.1.2 icmp_seq=4 Destination Host Unreachable
From 10.1.1.2 icmp_seq=5 Destination Host Unreachable

--- 10.1.1.1 ping statistics ---
5 packets transmitted, 0 received, +4 errors, 100% packet loss, time 4011ms

```

```
bagside@bagvapp:~$ ping 192.168.150.132
PING 192.168.150.132 (192.168.150.132) 56(84) bytes of data.
64 bytes from 192.168.150.132: icmp_seq=1 ttl=64 time=4.32 ms
64 bytes from 192.168.150.132: icmp_seq=2 ttl=64 time=0.332 ms
64 bytes from 192.168.150.132: icmp_seq=3 ttl=64 time=0.362 ms
64 bytes from 192.168.150.132: icmp_seq=4 ttl=64 time=0.320 ms
64 bytes from 192.168.150.132: icmp_seq=5 ttl=64 time=0.358 ms

--- 192.168.150.132 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 0.320/1.138/4.322/1.592 ms

```

can someone help me please.

Regards,

---

