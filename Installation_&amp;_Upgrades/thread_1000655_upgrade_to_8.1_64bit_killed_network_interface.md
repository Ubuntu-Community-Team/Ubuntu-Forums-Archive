---
title: "upgrade to 8.1 64bit killed network interface"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by nicsw on 2008-12-03
hello,

recently i upgraded ubuntu server 64bit to 8.1 and was experiencing some networking issues

it kept loosing the manual interface settings i checked the interface file and noticed that eth0 was missing so i manually added the setting as below

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
        address 192.168.10.200
        netmask 255.255.255.0
        network 192.168.10.0
        broadcast 192.168.10.255
        gateway 192.168.10.100

this seemed OK, but I had problems connect to the machine across the LAN

then suddenly the network stopped working altogether and the NIC did not show in the tool bar at the top

next i ran ifconfig and the card seemed to be alive and well

eth0      Link encap:Ethernet  HWaddr 00:13:8f:e0:18:b7  
          inet addr:192.168.10.200  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fee0:18b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5716 (5.7 KB)  TX bytes:468 (468.0 B)
          Interrupt:22 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89193 (89.1 KB)  TX bytes:89193 (89.1 KB)

still unable to resolve the problem I've have noticed other threads describing issues with networking on 8.1 but I don't seem to be able to resolve them

there were NVIDIA drivers installed but I also removed them but it made no difference

can anybody advise a course of action to get this server back on line ?

attached is a logfile over the last couple of days that may help somebody to help me resolve this

thanks for reading this and considering your reply

---

