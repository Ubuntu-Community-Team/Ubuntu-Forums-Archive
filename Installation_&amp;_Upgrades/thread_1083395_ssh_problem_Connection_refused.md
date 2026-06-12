---
title: "ssh problem: Connection refused"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by germ65 on 2009-02-28
This is my first post, sorry if that's not the appropriate forum. I tried to search for a solution, but could not find it.

Here's the problem:
- freshly installed Ubuntu 8.10 server with SSH server
- setup network for DHCP as described here:
[http://linux.about.com/od/ubusrv_doc/a/ubusg16t02.htm]("http://linux.about.com/od/ubusrv_doc/a/ubusg16t02.htm")
- Ubuntu computer connected to same router as iMac
- ssh from iMac to Ubuntu works fine using dynamically assigned IP address
- change network configuration on Ubuntu machine to static address
- ssh from iMac shows connection refused!

Why?

---

### Post by DGortze380 on 2009-02-28
> **germ65 said:**
> This is my first post, sorry if that's not the appropriate forum. I tried to search for a solution, but could not find it.

Here's the problem:
- freshly installed Ubuntu 8.10 server with SSH server
- setup network for DHCP as described here:
[http://linux.about.com/od/ubusrv_doc/a/ubusg16t02.htm]("http://linux.about.com/od/ubusrv_doc/a/ubusg16t02.htm")
- Ubuntu computer connected to same router as iMac
- ssh from iMac to Ubuntu works fine using dynamically assigned IP address
- change network configuration on Ubuntu machine to static address
- ssh from iMac shows connection refused!

Why?

On your ubuntu box, can you post the output of:

ifconfig -a
cat /etc/network/interfaces

Also, if you know the following information (can typically be obtain from your routers configuration page)

router's ip address
netmask (subnet)
addresses in dhcp range

---

### Post by germ65 on 2009-02-28
> **DGortze380 said:**
> On your ubuntu box, can you post the output of:

ifconfig -a
cat /etc/network/interfaces

Also, if you know the following information (can typically be obtain from your routers configuration page)

router's ip address
netmask (subnet)
addresses in dhcp range

Wow, that's a really fast response. In the meantime, I have reverted the Ubuntu machine to DHCP, and now I can ssh in again. 

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:21:1b:d2:e6  
          inet addr:192.168.2.148  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe1b:d2e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9396 errors:0 dropped:2548301407 overruns:0 frame:0
          TX packets:5882 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10205377 (10.2 MB)  TX bytes:489836 (489.8 KB)
          Interrupt:221 

eth1      Link encap:Ethernet  HWaddr 00:24:21:1b:d2:e7  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:184 (184.0 B)  TX bytes:184 (184.0 B)

$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
#address 192.168.2.3
#netmask 255.255.255.0
#gateway 192.168.2.1

router's ip address: 192.168.2.1
netmask (subnet): 255.255.255.0
addresses in dhcp rang  192.168.2.100 start address with a max. of 50 users

---

### Post by germ65 on 2009-03-01
Meanwhile, I have installed Webmin and changed the network settings to static from within Webmin. 

The problem persists. As soon as I set the Ubuntu machine to Static IP, I cannot ssh in anymore. 

Any ideas?

---

### Post by germ65 on 2009-03-01
I found out that I had a webcam with the same address on my network. 

Everything works fine now.

Very sorry for the confusion/waste of time.

---

