---
title: "Cannot connect to WEP network"
date: 2009-10-14
forum: Hardware
---

### Post by flightless bird on 2009-10-14
I cannot connect to the wireless network at work, athough I have no problems at home. I have connected to WEP networks before, and my wireless functions perfectly well (using Broadcom STA proprietry driver) in most situations. 
    However, and to my eternal frustration I cannot connect to the network at work, although I can see it fine, seemingly handshake with it, but the connection process always seems to break down when requesting an ip address. The same hardware connects ok when I boot into windows, but for the obvious reasons, I'd prefer not to have to do that. 
    I have little access to good IT support (it's a school, and not known for understanding of its infrastructure). The router seems to be a belkin model of some description. The ifconfig output is fairly boring, but it is posted below if you are interested.

Any suggestions welcomed.

lshw at [pastebin.com/fdf2d464]("http://pastebin.com/fdf2d464")

output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1b:38:2e:f5:a9  
          inet addr:192.168.135.180  Bcast:192.168.135.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe2e:f5a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:272357024 (272.3 MB)  TX bytes:15580101 (15.5 MB)
          Interrupt:16 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:66:fa:a5  
          inet6 addr: fe80::21a:73ff:fe66:faa5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:251227 errors:0 dropped:0 overruns:0 frame:1767988
          TX packets:170692 errors:546 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:311245276 (311.2 MB)  TX bytes:18241498 (18.2 MB)
          Interrupt:18 

eth1:avahi Link encap:Ethernet  HWaddr 00:1a:73:66:fa:a5  
          inet addr:169.254.9.84  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1049420 (1.0 MB)  TX bytes:1049420 (1.0 MB)

pan0      Link encap:Ethernet  HWaddr 5e:d0:17:d4:1f:a6  
          UP BROADCAST RUNNING MULTICAST  MTU:1000  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:46634 (46.6 KB)

pan0:avahi Link encap:Ethernet  HWaddr 5e:d0:17:d4:1f:a6  
          inet addr:169.254.7.53  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1000  Metric:1


```

---

### Post by Dark_Stang on 2009-10-14
You are choosing the appropriate key type, correct? Hex, Ascii, etc.

---

### Post by Binoy918 on 2009-10-15
I have the same problem with my Dell 1525 on Ubuntu 9.04 Jaunty. I am able to connect to open wifi but not to encrypted ones. I am using broadcom restricted drivres. Has anyone connected to WEP or WPA networks using broadcom restricted drivers?

---

### Post by Niko Johnson on 2009-10-15
yeah i have... but i dont know what the problem is, i just type in the wep key and im in. i never had any problems with it, if you want to get down and dirty try to hack YOUR OWN NETWORK with backtrack. backtrack can tell you exactly whats going on

---

### Post by Dark_Stang on 2009-10-16
> **Binoy918 said:**
> I have the same problem with my Dell 1525 on Ubuntu 9.04 Jaunty. I am able to connect to open wifi but not to encrypted ones. I am using broadcom restricted drivres. Has anyone connected to WEP or WPA networks using broadcom restricted drivers?

Mine works just fine.

---

