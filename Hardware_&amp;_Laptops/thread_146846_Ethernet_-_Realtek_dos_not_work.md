---
title: "Ethernet - Realtek dos not work"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by manfredfr on 2006-03-19
Hi,

I did a fresh installation of ubuntu 5.1. 
Everything seams to work fine except the network is not working. 

The ethernet card is a  realtek compatible card which is working under other OSs on the same HW (debian, windows XP).

Here is a list of some things I tryed already:

```


-------- PCI info -------- 
root@ubuntu:~# lspci | grep -i eth
0000:00:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

-------- physical layer -------- 
root@ubuntu:~# mii-tool eth0
eth0: negotiated 100baseTx-FD flow-control, link ok

-------- software driver --------
root@ubuntu:~# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:E0:7D:74:1C:17
          inet addr:10.1.1.2  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:7dff:fe74:1c17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000


-------- driver loaded --------
root@ubuntu:~# lsmod | grep mii
mii                     5248  2 8139too,8139cp


-------- find router -------- 
root@ubuntu:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth0


-------- ping router --------
root@ubuntu:~# ping 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
From 10.1.1.2 icmp_seq=2 Destination Host Unreachable
From 10.1.1.2 icmp_seq=3 Destination Host Unreachable
From 10.1.1.2 icmp_seq=4 Destination Host Unreachable
From 10.1.1.2 icmp_seq=6 Destination Host Unreachable
From 10.1.1.2 icmp_seq=7 Destination Host Unreachable
From 10.1.1.2 icmp_seq=8 Destination Host Unreachable

--- 10.1.1.1 ping statistics ---
9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 8000ms
, pipe 3

-------- ifconfig after ping --------
root@ubuntu:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:7D:74:1C:17
          inet addr:10.1.1.2  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:7dff:fe74:1c17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:546915 (534.0 KiB)  TX bytes:546915 (534.0 KiB)

-------- /etc/network/interface --------
root@ubuntu:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 10.1.1.2
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        gateway 10.1.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.1.1.1

```

Any ideas or hints?

BTW: I am suprized about the problem because debian is working fine.

Thx 
Manfred

---

### Post by dermotti on 2006-03-19
Looks like it sees the card, but you have a funky ip address... Did you set up DHCP? **EDIT** nvm I see you are using static.....

I guess i would try using DHCP if possible and see if that fixes it, maybe something in your config is messed. Otherwise you could try a different kernel....but to me it looks like it sees the card alright.

---

### Post by manfredfr on 2006-03-19
Hi dermotti,

well I tried this already but it doesnt work, cause the card cant reach the router. 

Why do you think the ip address is fancy?

Cheers
Manfred

---

### Post by dermotti on 2006-03-19
Hmm, mine works perfect like this:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1

---

### Post by manfredfr on 2006-03-19
hmmm the difference is the hotplug entry.

I am going to try that ...

---

### Post by manfredfr on 2006-03-19
the card was not longer listed within ifconfig after i removed the following lines from /etc/network/interface:

```

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

```
I think I have to figure out whats up with hotplug. Why do I need an hodplug entry? How to configure the card without hotplug?

---

### Post by quaff on 2006-03-19
I've got the same problem with my eth0... 

i popped in an old SuSE 9.2 Live CD of mine, and it detected my eth0 and connected to my router properly (DHCP).

but on Ubuntu (kubuntu too.. and the live cds), it doesn't seem to want to connect to my router.. 
but it doesn't seem to be just Ubuntu.. i threw on Gentoo 2005.1.. and it couldn't connect either..
I'm gonna try slackware and debian, then i'll report back whether it works or not.. if someone wants some debug info or anything.. just tell me how i can help :)

---

### Post by quaff on 2006-03-19
works in debian O.o

---

### Post by manfredfr on 2006-03-20
well I deactivated the hotplugable service - still not working :-(

I created a bug entry ( Bug #35683 ) hopfully someone will have a closer look.

thanks for your help folks.
Manfred

---

### Post by Horndog on 2006-03-20
What IP do you use to access your router menu?

---

### Post by manfredfr on 2006-03-20
> What IP do you use to access your router menu?

Well, 10.1.1.1 the router address.

---

### Post by Horndog on 2006-03-20
Did you install ubuntu with the network card plugged in to the router using a cat5 cable?


*EDIT*

> -------- ping router --------
root@ubuntu:~# ping 10.1.1.1
[color=red]PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.[/color]
From 10.1.1.2 icmp_seq=2 Destination Host Unreachable
From 10.1.1.2 icmp_seq=3 Destination Host Unreachable
From 10.1.1.2 icmp_seq=4 Destination Host Unreachable
From 10.1.1.2 icmp_seq=6 Destination Host Unreachable
From 10.1.1.2 icmp_seq=7 Destination Host Unreachable
From 10.1.1.2 icmp_seq=8 Destination Host Unreachable



If your router is 10.1.1.1 then the ping was successful

---

### Post by manfredfr on 2006-03-20
> Did you install ubuntu with the network card plugged in to the router using a cat5 cable?

Yes.

and mii-tool shows a physical link:
```
root@ubuntu:~# mii-tool eth0
eth0: negotiated 100baseTx-FD flow-control, **link ok**
```

I am using Grub to boot debian with the same hardware, card, cable and router and it works.

---

### Post by Horndog on 2006-03-20
Can you access the Internet? Also, what other computers and OS's do you have on your local network.

---

### Post by manfredfr on 2006-03-20
> Can you access the Internet? Also, what other computers and OS's do you have on your local network.

I can access the internet with the same computer by booting Windows XP or debian (Grub boot).

1 computer 1 router

---

### Post by Horndog on 2006-03-20
Two things to try:

```
ifdown eth0
```

then

```
ifup eth0
```

If that doen't work then try rebooting the router.

---

### Post by manfredfr on 2006-03-21
```

root@ubuntu:~# ifdown eth0
root@ubuntu:~# ifup eth0

root@ubuntu:~# ping 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
From 10.1.1.2 icmp_seq=2 Destination Host Unreachable
From 10.1.1.2 icmp_seq=3 Destination Host Unreachable
From 10.1.1.2 icmp_seq=4 Destination Host Unreachable
From 10.1.1.2 icmp_seq=6 Destination Host Unreachable
From 10.1.1.2 icmp_seq=7 Destination Host Unreachable

```

Router still not pingable.
Router rebooted still not pingable.
I pluged a 2nd Computer (MacOsx ip=10.1.1.3) on the router. Router works fine. Router is pingable ubuntu is not pingable.

---

### Post by manfredfr on 2006-03-21
deleted

---

### Post by manfredfr on 2006-03-21
Solved it.

The problem is was acpi related. The card works as expected after booting with boot option 

```
pci=noacpi
```

Thanks for your help folks
Manfred

---

