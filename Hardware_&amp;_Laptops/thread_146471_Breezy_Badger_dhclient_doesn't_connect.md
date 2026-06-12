---
title: "Breezy Badger dhclient doesn't connect"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by Finster101 on 2006-03-18
Hi all,

First I'd like to say I've read through many of the posts of people with similar problems but none seem to match mine exactly.  Although I did try some of the suggestions that I thought might help with no sucess.  Here's my problem:

I installed Breezy Badger 5.10 on my new computer and it will not connect to the Internet since it never receives an IP address.  I have another computer that has Fedora Core 4 and Win XP installed.  This machine will connect with no problem.  To remove some of the variables and diagnose this problem I have been connecting each machine through the very same cable directly into my cable modem.  To see if the new computer's network card was behaving I connected the two computers together with a crossover cable and was able to setup each card and ping back and forth.  So I believe that the network card is functioning.  Example:
     Machine #1 ifconfig eth0 192.168.1.1 up
     Machine #2 ifconfig eth0 192.168.1.2 up
     Machine #1 ping 192.168.1.2 
     Machine #2 ping 192.168.1.1   
     (This worked)

Somehow I am thinking that FC4 dhclient is doing something different than Ubuntu?  I've tried to discover what, but I am lost in all the connection scripts and there doesn't seem to be a dhclient.conf file on this system.

Here is my info on the machine and the usual linux command output
emachines T3406
celeron 340 D 2.93Ghz
80G drive
Intel PRO 10/100 network card
Motorola Surfboard SB4200 cable modem (Optimum Online, NY cable company)

$ sudo su
# dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/(my mac)
Sending on   LPF/eth0/(my mac)
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

# ifconfig 
eth0      Link encap:Ethernet  HWaddr (my mac)
          inet6 addr: fe80::213:20ff:fe2b:ef1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1307498 (1.2 MiB)  TX bytes:25854 (25.2 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:658726 (643.2 KiB)  TX bytes:658726 (643.2 KiB)

# dmesg | grep eth0
[4294678.294000] e100: eth0: e100_probe: addr 0xff8ff000, irq 20, MAC addr (my mac)
[4294702.698000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[4294901.535000] eth0: no IPv6 routers present

# lspci | grep Eth
0000:01:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 02)

Anyone have any suggestions?
Thanks
Brian

---

### Post by ranf on 2006-03-19
I'm not sure if it works. Worth a try anyway.
Try disabling IPv6:
[https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4)

---

### Post by infoseeker on 2006-03-19
Every now and then I have the same problem.  What sorts me out is to disable internet sharing on the pc that does the dialing out (happens to be winxp in my case) and then re-enable the sharing. Then execute 'dhclient' in a terminal.  This normally sorts out MY problem.

---

### Post by sherlock-holmes on 2006-03-21
[QUOTE=infoseeker]Every now and then I have the same problem.  What sorts me out is to disable internet sharing on the pc that does the dialing out (happens to be winxp in my case) and then re-enable the sharing. Then execute 'dhclient' in a terminal.  This normally sorts out MY problem.[/QUOTE]


i have the similar errors and more,,,,,

[PHP]name@comp:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 9006
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:24:20:2d
Sending on   LPF/eth1/00:12:f0:24:20:2d
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
Trying recorded lease 192.168.1.101
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
connect: Network is unreachable
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
No working leases in persistent database - sleeping. [/PHP]

what permisson is it talking about? i guess its not anything to do with sudo?
and the Network window DNS doesnt show any DNS addresses .... any  help ?

---

