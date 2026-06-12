---
title: "Network card problems"
date: 2008-08-26
forum: Hardware
---

### Post by dmiller40 on 2008-08-26
I'm running ubuntu live cd on a gateway profile 5. I have manually set the ip address and no connection. In my network tools the eth0 is sending and receiving packets but my harward address, multicast, MTU, link speed, & state all say unavailable.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:6F:48:5A  
          inet6 addr: fe80::2e0:b8ff:fe6f:485a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:230635 (225.2 KB)  TX bytes:6179 (6.0 KB)
          Base address:0x9000 Memory:fc000000-fc020000 

```

thanks
dm

---

### Post by Sam Lars on 2008-08-26
It doesn't appear that your card has an IP address, how are you setting it?

---

### Post by dmiller40 on 2008-08-26
I think its called gnome network manager, that computer icon on the top panel at the right.

dm

---

### Post by Sam Lars on 2008-08-26
What IP address are you setting?  Are you able to DHCP?

---

### Post by dmiller40 on 2008-08-26
I'm not able to use DHCP right now, I'm at work and have to set the ip, gateway, and dns.

dm

---

### Post by Sam Lars on 2008-08-26
While you're in the network manager, can you check and then uncheck the box for the card to see if that will get it to work?  You could also try a reboot after applying the settings.

---

### Post by Crafty Kisses on 2008-08-26
Post the following output:
```
lshw -C network
```

---

