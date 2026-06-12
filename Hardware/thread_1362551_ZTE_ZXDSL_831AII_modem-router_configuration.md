---
title: "ZTE ZXDSL 831AII modem-router configuration"
date: 2009-12-23
forum: Hardware
---

### Post by ssj6akshat on 2009-12-23
Hello.My Router Config page 192.168.1.1 is not working in Ubuntu but it is working on Windows.My router is ZTE ZXDSL 831AII.
There is a typo in the title.

---

### Post by scottuss on 2009-12-23
Open a Terminal and try to ping 192.168.1.1

```
ping 192.168.1.1
```

hit Ctrl-C to stop the pinging.

What do you get from that?

Edit: Having said that, my router doesn't respond to ping. Type ipconfig into a Terminal and post the results

```
 ipconfig 
```

---

### Post by ssj6akshat on 2009-12-23
I get this

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
^C
--- 192.168.1.1 ping statistics ---
23 packets transmitted, 0 received, 100% packet loss, time 22175ms

---

### Post by scottuss on 2009-12-23
Right, so what do you get from ipconfig?

---

### Post by ssj6akshat on 2009-12-23
Did you mean ifconfig

eth0      Link encap:Ethernet  HWaddr 00:50:04:bd:ab:fe  
          inet6 addr: fe80::250:4ff:febd:abfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78878695 (78.8 MB)  TX bytes:5593766 (5.5 MB)
          Interrupt:22 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9772 (9.7 KB)  TX bytes:9772 (9.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.196.211.58  P-t-P:117.196.208.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:66640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:77200838 (77.2 MB)  TX bytes:4337784 (4.3 MB)

---

### Post by scottuss on 2009-12-23
I did indeed mean ifconfig! 

Too much time fixing Windows! :P


OK, so you're connected to an ADSL modem right? You have a ppp connection that is active (ppp0)

The IP address of ppp0 is provided by your ISP. Did you put this PC in the DMZ for some reason?

---

### Post by ssj6akshat on 2009-12-23
What is DMZ?

---

### Post by scottuss on 2009-12-23
Perhaps not then. It seems your Ubuntu PC has a public IP address, meaning that it is either not connected to your router, or it has been placed in the DMZ, meaning that it is not protected NAT.

I would go into the admin interface on your Windows PC and check how the router is configured.

If you can log into the admin interface on your Windows PC and take some screenshots of the config, we might be able to see how it's all set up and help you get it sorted.

Daft question: Is this Ubuntu PC plugged directly into the router by an ethernet cable?

---

### Post by ssj6akshat on 2009-12-23
yes it is plugged directly from ethernet.

---

### Post by ugm6hr on 2009-12-24
I have renamed the thread to something more useful

---

