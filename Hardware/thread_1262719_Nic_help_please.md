---
title: "Nic help please"
date: 2009-09-10
forum: Hardware
---

### Post by cameron365 on 2009-09-10
I have ubuntu 8.04 server which i have moved the HDD to new hardware but now there is no NIC! when i use
lspci
i can see my NIC name, how can i install it?
is there any thing that can find new hardware and install it.
it seems ubuntu know the name of NIC

---

### Post by trundlenut on 2009-09-10
you'll will probably find because you have chnaged hardware the new nic has a different mac address so it will show up as a different device i.e. eth1 instead of eth0

what does the following command show?

```
sudo lshw -C network
```

---

### Post by cameron365 on 2009-09-10
> **trundlenut said:**
> you'll will probably find because you have chnaged hardware the new nic has a different mac address so it will show up as a different device i.e. eth1 instead of eth0

what does the following command show?

```
sudo lshw -C network
```

here the resault of lshw -C network

*-network
       descriptions: Ethernet interface
       product: 82801G ( ICH7 Family) LAN Controller
       vendor: Intel Corporation
       phisical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth1
       version: 01
       serial: 00:16:76:bd:10:54
       size: 100MB/s
       capacity: 100 MB/s
       width: 32 bits
       clock: 33MHz
       Capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver-e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=10.10.10.10 latency=32 link=yes maxlatency=56 mingnt=8 mudule-e100 multicast=yes port=MII speed=100MB/s

and a lot of lines ....
thanks for your help

---

### Post by ukripper on 2009-09-10
can you post output of following command:
```
ifconfig
```

---

### Post by trundlenut on 2009-09-10
> **cameron365 said:**
> here the resault of lshw -C network

*-network
       descriptions: Ethernet interface
       product: 82801G ( ICH7 Family) LAN Controller
       vendor: Intel Corporation
       phisical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth1
       version: 01
       serial: 00:16:76:bd:10:54
       size: 100MB/s
       capacity: 100 MB/s
       width: 32 bits
       clock: 33MHz
       Capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver-e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=10.10.10.10 latency=32 link=yes maxlatency=56 mingnt=8 mudule-e100 multicast=yes port=MII speed=100MB/s

and a lot of lines ....
thanks for your help

So that is saying that your network connection is eth1.  So as ukripper asked what does ifconfig report?

---

### Post by cameron365 on 2009-09-10
> **trundlenut said:**
> So that is saying that your network connection is eth1.  So as ukripper asked what does ifconfig report?

i go to /etc/network/interface and change the eth0 to eth1 and then reboot the server now system is up and running but when i want to ping gateway it doesnt ping but i cant ping the XEN Guests!
:(:(Please help me why the connection is disconnected?

---

### Post by ukripper on 2009-09-10
> **cameron365 said:**
> i go to /etc/network/interface and change the eth0 to eth1 and then reboot the server now system is up and running but when i want to ping gateway it doesnt ping but i cant ping the XEN Guests!
:(:(Please help me why the connection is disconnected?

you need to add your gateway in **/etc/resolv.conf** file

and add following line:
> nameserver yourgatewayip
replace yourgetwayip with gateway ip address

---

### Post by cameron365 on 2009-09-10
> **ukripper said:**
> you need to add your gateway in **/etc/resolv.conf** file

and add following line:

replace yourgetwayip with gateway ip address


resolve.conf? it os for DNS, isnt it?
i just cant ping my gateway's IP.

---

### Post by trundlenut on 2009-09-10
are you trying to ping by ip address or name?

What is the output from ifconfig?

---

### Post by ukripper on 2009-09-10
> **cameron365 said:**
> resolve.conf? it os for DNS, isnt it?
i just cant ping my gateway's IP.

have you tried as suggested above with your gateway ip in resolv.conf?

---

### Post by cameron365 on 2009-09-10
> **trundlenut said:**
> are you trying to ping by ip address or name?

What is the output from ifconfig?

Of course i ping using IP address.
#ifconfig eth1
eth1  Link encap:Ethernet    HWaddr 00:16:76:bd:10:54
    inet addr:10.10.10.10   Bcast:10.10.10.127 Mask:255.255.255.240
      inet6 addr: fe80::216:------------- Scope: Link
    UP BROADCASR RUNNIING MULTICAST MTU:1500 Metric:1
    RX packets:14 errors:0 dropped:0 overruns:0 frame:0
    TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX byte:392  (392.0 B) TX byte:1728 (1.6 KB)

---

### Post by trundlenut on 2009-09-10
well it would appear that you are connected.

Can you ping the server from another machine?

---

### Post by cameron365 on 2009-09-10
> **trundlenut said:**
> well it would appear that you are connected.

Can you ping the server from another machine?

NO i cant ping the server from another machine but from my Mikrotik route i can see the MAC address of server in arp section. but i cant ping the server

---

### Post by trundlenut on 2009-09-10
> **ukripper said:**
> you need to add your gateway in **/etc/resolv.conf** file

and add following line:

replace yourgetwayip with gateway ip address

Have you tried/checked this?

---

### Post by ukripper on 2009-09-10
> **trundlenut said:**
> Have you tried/checked this?

works for me!

---

### Post by cameron365 on 2009-09-10
> **ukripper said:**
> works for me!

what is the related between /etc/resove.conf to the network connection. my problem is i cant ping my gateway's IP address, i dont have problem with dns.

---

### Post by cameron365 on 2009-09-11
at last i put new NIC and turn on the server and used ifconfig to see new nic but nothing appear then use used
ifconfig eth4 up
and then i see there is NIC on eth4!!! i set ip and then everything goes back and working well!!!
WHAT IS IT?
Can i change it back to eth0 instead of eth4?
how?
please help me why this happen and why my old NIC dosnt work in ubuntu?

---

