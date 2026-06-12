---
title: "connected to two networks at once"
date: 2008-11-25
forum: General Help
---

### Post by M4rotku on 2008-11-25
Hello all,

Yesterday, I upgraded to 8.10.  Previously both my Ethernet and wireless worked fine and they worked one at a time.  Now, when I have both networking and wireless enabled, my computer attempts to connect to both of them at the same time.  As far as I can tell, it successfully does so.  However, when I am connected to both, I can not use the Internet via either.  In order to be able to use the Internet, I either have to unplug the Ethernet cable or turn off my wireless card.

What is causing this problem?  Is there any way that I could go about fixing this?  

Much thanks,
M4rotku

---

### Post by ilrudie on 2008-11-25
Post the results of 'ifconfig -a' and 'netstat -rn'

---

### Post by M4rotku on 2008-11-25
ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:1b:24:b8:a4:cc  
          inet addr:192.168.201.23  Bcast:192.168.201.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:57017822 (57.0 MB)  TX bytes:2482292 (2.4 MB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61004 (61.0 KB)  TX bytes:61004 (61.0 KB)

pan0      Link encap:Ethernet  HWaddr 2a:ff:af:e5:3b:2a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:de:d1:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-DE-D1-93-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



netstat -rn

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.201.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.201.1   0.0.0.0         UG        0 0          0 eth0

---

### Post by ilrudie on 2008-11-25
Your wireless connection doesn't list an IP and doesn't appear anywhere in the routing tables.  Was your wireless on and connected when you captured the above output?  If not please make sure you have both wired and wireless ethernet on and that you are experiencing the issue getting to the internet when you capture output from the commands and then repost to output.

---

### Post by M4rotku on 2008-11-27
Both were not connected.  The next time I'm in that situation, I'll record the new results and post them.

---

### Post by M4rotku on 2008-12-02
Ok, I had the problem again and so here are the results with both of the networks connected.

> joey@joey-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:24:b8:a4:cc  
          inet addr:192.168.201.23  Bcast:192.168.201.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84583 (84.5 KB)  TX bytes:22478 (22.4 KB)
          Interrupt:219 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26684 (26.6 KB)  TX bytes:26684 (26.6 KB)

pan0      Link encap:Ethernet  HWaddr fe:c1:47:9b:f7:39  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:de:d1:93  
          inet addr:192.168.209.18  Bcast:192.168.211.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20285 (20.2 KB)  TX bytes:2210 (2.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-DE-D1-93-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

joey@joey-laptop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.201.0   0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.208.0   0.0.0.0         255.255.252.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.201.1   0.0.0.0         UG        0 0          0 eth0
joey@joey-laptop:~$ 


Also, another major problem that may be associated with this one.  The light on my wireless switch, which now utilizes both available colors to indicate conectivity, keeps flickering between the two colors.  Furthermore, when this flickering gets really bad, my caps lock button begins to flicker and the entire computer freezes from which I have to reboot.  I don't know if this is related or not, it's almost enough to make me attempt to go back to 8.04.  We'll have to see if it continues.

---

### Post by elixr on 2008-12-02
These adapters are on different subnets.  When you connect with one or the other, do they both have internet connectivity, and only when both are enabled then you lose both?

Are they both supposed to be on the same network?

---

### Post by M4rotku on 2008-12-02
They connect to two different networks.  When both are connected, as far as I can discern, only the wireless connection works.  I am assuming this because when I try to connect to the Internet, I have to go through the login page that is necessary for the wireless connection.

---

### Post by ilrudie on 2008-12-02
I was figuring it was a routing issue with the two different networks.  Maybe wlan removing the default route but failing to add a new one or something.  All the routing looks normal though.  wlan0 shouldn't be involved unless you are trying to get to something on the 192.168.208.0 subnet.  Perhaps this is a bug causing an internal conflict between the wired and wireless networking.  Have you checked the error logs while this issue is occurring?  Try tail -f on /var/log/debug or /var/log/messages or /var/log/kern.log and see if anything is showing up.  If you prefer gui use System>Administration>System Log.  Have you searched for a bug report similar to this?  If you can't find one like this you might want to submit one.

---

### Post by M4rotku on 2008-12-02
The system log showed nothing.  The oddity is that previous to the upgrade to 8.10, it had only connected to one network at once.  Is there any way to change this setting?

---

### Post by ilrudie on 2008-12-02
There is probably a way to change this setting but I have no clue where it would be.

---

### Post by HermanAB on 2008-12-02
The 'working' network is controlled by the default route in the routing table.  If you have two network interfaces active with DHCP, then the one that comes up last will 'win' and will set the default route.  You can see what is going on with the route command:
$ sudo route

You should maybe read the Advanced Routing Howto on tldp.org.

Cheers,

Herman

---

