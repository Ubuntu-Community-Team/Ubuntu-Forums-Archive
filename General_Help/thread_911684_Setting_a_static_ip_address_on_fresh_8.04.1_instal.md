---
title: "Setting a static ip address on fresh 8.04.1 installation"
date: 2008-09-05
forum: General Help
---

### Post by milasch on 2008-09-05
Hello,

I've just installed Ubuntu on my desktop computer, and the first thing I wanted to do was to assign a static ip address to it.

So I followed the obvious: 

1 - Went to System->Administration->Network Tools. 
2 - Changed Network Device to ETH0
3 - Clicked Configure. Got this error message:
[ATTACH]84214[/ATTACH]
4 - Clicked "Close", also closed the Network Tools screen.
5 - Went to System->Administration->Network
6 - Under Connections Tab clicked Unlock
7 - Typed in my password
8 - Selected Wired Connection then Properties
9 - Noticed the only way to change the shown options was to disable the "Roaming Mode", so I did it.
10 - Selected Static IP in Configuration.
11 - Typed my IP address, Subnet Mask and Gateway to look like this:
[ATTACH]84217[/ATTACH]
12 - Clicked OK/Close on every window, and noticed I lost internet connection. So I went to the terminal and typed:
```

milasch@milasch-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:7e:57:8a  
          inet6 addr: fe80::21f:c6ff:fe7e:578a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:810373 (791.3 KB)  TX bytes:145282 (141.8 KB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86700 (84.6 KB)  TX bytes:86700 (84.6 KB)

milasch@milasch-desktop:~$ ping 192.168.0.1
connect: Network is unreachable

```

As you can see there is no ipv4 settings under eth0.

When I go back and select "Roaming Mode" it starts functioning again:
```

milasch@milasch-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:7e:57:8a  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe7e:578a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:812743 (793.6 KB)  TX bytes:148687 (145.2 KB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86700 (84.6 KB)  TX bytes:86700 (84.6 KB)

milasch@milasch-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.84 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=1.00 ms

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 1.009/1.429/1.849/0.420 ms

```

I've had the same problem on my laptop, I fixed by messing with the /etc/network/interfaces file, but it was pure luck... I would like to understand this properly instead of just messing and crossing my fingers hoping it will work.

My "Roaming Mode" is enabled, and I have the following /etc/network/interfaces file looks like this:
```

milasch@milasch-desktop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```

It looks like this when I set static ip:
```

milasch@milasch-desktop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

```

Also, another work around would be to do:
```

milasch@milasch-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:7e:57:8a  
          inet6 addr: fe80::21f:c6ff:fe7e:578a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2273473 (2.1 MB)  TX bytes:407878 (398.3 KB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87384 (85.3 KB)  TX bytes:87384 (85.3 KB)

milasch@milasch-desktop:~$ sudo ifdown eth0
sudo: unable to resolve host milasch-desktop
[sudo] password for milasch: 
RTNETLINK answers: No such process
SIOCDELRT: No such process
milasch@milasch-desktop:~$ sudo ifup eth0
sudo: unable to resolve host milasch-desktop
milasch@milasch-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:7e:57:8a  
          inet addr:192.168.0.169  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe7e:578a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2273473 (2.1 MB)  TX bytes:411213 (401.5 KB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88080 (86.0 KB)  TX bytes:88080 (86.0 KB)

```

But then I have to do this every time I boot my system. It's not quite what I want.

Does anyone knows how to fix this? Is this a general bug or it's a hardware related problem? Because I googled for an answer for a while and even posted here before and no one replied, so I assume it's not a common issue.

Thanks

---

### Post by milasch on 2008-09-05
I had similar issues with Fedora 9, and the work around was to enable a service called "network" and remove the package networkmanager. But I can't find both thins in Ubuntu.

---

