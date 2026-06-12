---
title: "HELP: Internet Connection Problem"
date: 2008-11-18
forum: General Help
---

### Post by DaBigWig809 on 2008-11-18
I just recently installed Ubuntu from Windows XP Pro. The internet connection works at times but then it just doesn't. When I check what's wrong it says nothing is wrong. I also go on (192.168.1.1) and restart connecting/setup again but nothing works. 

Does anyone know what is happening ? 

I setup Ubuntu fine with no problems, internet was working fine before. This happened last night again it stopped working but then it worked again. I just don't want it to keep happening, does anyone have a clue because I don't ?:confused:

---

### Post by DaBigWig809 on 2008-11-18
I'm using Verizon DSL in NYC. A Westell 7500.

---

### Post by Peter09 on 2008-11-18
When it stops working type the following command in the terminal

```
ifconfig
```

if you post the output  it will give us an idea as to what is happening.

You can stop and start networking with the commands

```
sudo /etc/init.d/networking start
```

```
sudo /etc/init.d/networking stop
```

```
sudo /etc/init.d/network restart
```

see if that does anything.

---

### Post by DaBigWig809 on 2008-11-18
Okay, this is what comes out when I type ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:19:21:35:b2:20  

          inet addr:192.168.1.30  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::219:21ff:fe35:b220/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:1958 errors:0 dropped:0 overruns:0 frame:0

          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:149883 (149.8 KB)  TX bytes:15381 (15.3 KB)

          Interrupt:20 Base address:0xec00 



eth1      Link encap:Ethernet  HWaddr 00:18:3a:82:e1:43  

          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::218:3aff:fe82:e143/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:2775 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1090 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:162312 (162.3 KB)  TX bytes:89115 (89.1 KB)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:242 errors:0 dropped:0 overruns:0 frame:0

          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:15140 (15.1 KB)  TX bytes:15140 (15.1 KB)

---

### Post by Peter09 on 2008-11-18
You appear to have two interfaces connected on the same network, is that correct?

---

### Post by cariboo on 2008-11-18
It looks like you have two network card cinnection to your dsl modem. Unless you are using the two nic for a reason. Try disabling one of them in the BIOS.

If you are using the two nics for connection sharing, You will have to give the one nic that the rest of the network is connected to a static ip address in a different netblock.

Jim

---

### Post by DaBigWig809 on 2008-11-18
Yes, I have two computers. I'm on this one through an access point/wireless Windows XP PRO. The other one is mines running Ubuntu 8.10.

This one works fine even though its connected to the same modem through a wireless connection. My Linux where the modem is connected doesn't work, it works but then it don't. All connections, it says, are connected and everything seems fine, just I open Firefox and nothing comes up, or Google comes up but I can't go to another site.

---

### Post by DaBigWig809 on 2008-11-18
> **cariboo907 said:**
> It looks like you have two network card cinnection to your dsl modem. Unless you are using the two nic for a reason. Try disabling one of them in the BIOS.

If you are using the two nics for connection sharing, You will have to give the one nic that the rest of the network is connected to a static ip address in a different netblock.

Jim

I'm new to Ubuntu, how do I go about this ?

---

### Post by Peter09 on 2008-11-18
Yes, but you appear to have to connections to your Linux box, why have you done that? That is most probably the problem.

---

### Post by DaBigWig809 on 2008-11-18
> **Peter09 said:**
> Yes, but you appear to have to connections to your Linux box, why have you done that? That is most probably the problem.

I'm really sorry, but what are you talking about ? Linux Box ? 

I'm running Windows XP Pro on one computer and Ubuntu 8.10 on the other, both are desktops. The Ubuntu 8.10 is where my modem/DSL is at and the Windows XP Pro is where I have a Wireless USB Adapter to get a connection from the modem/DSL.

Can someone _explain _how I fix the problem ?

---

### Post by Peter09 on 2008-11-18
Linux Box = Ubuntu

The output of ifconfig shows that you appear to have two network interfaces (cables) connected to your Ubuntu machine. Is this the case?

---

### Post by DaBigWig809 on 2008-11-18
Not at all. I have 1 Cable.

I do have this computer I am using now connected to the same modem/DSL I have connected to the Linux Box. 

The modem is connected via ethernet to the computer.

This computer I have connected using a Wireless USB Adapter.

---

### Post by DaBigWig809 on 2008-11-18
Nobody wants to help, how weird is this problem? I really want to fix it, I've tried everything. 

Please help.

---

### Post by Peter09 on 2008-11-18
I am puzzled by the following lines in your output of ifconfig

> eth0 Link encap:Ethernet HWaddr 00:19:21:35:b2:20

inet addr:192.168.1.30 Bcast:192.168.1.255 Mask:255.255.255.0

and

> eth1 Link encap:Ethernet HWaddr 00:18:3a:82:e1:43

inet addr:192.168.1.33 Bcast:192.168.1.255 Mask:255.255.255.0

This shows two IP addresses 192.168.1.30 and 192.168.1.33 which are both active on your Ubuntu machine.

---

### Post by DaBigWig809 on 2008-11-18
> **Peter09 said:**
> I am puzzled by the following lines in your output of ifconfig



and



This shows two IP addresses 192.168.1.30 and 192.168.1.33 which are both active on your Ubuntu machine.

Could it be that I have 2 computers connected to one modem/DSL ? One is via Ethernet and this one is via Wireless USB Adapter.

---

### Post by Peter09 on 2008-11-18
When you talk about a modem is it a modem/router? I guess it must be if it is supporting your wireless machine.

---

### Post by DaBigWig809 on 2008-11-18
> **Peter09 said:**
> When you talk about a modem is it a modem/router? I guess it must be if it is supporting your wireless machine.

Yes, Modem Router (Westell 7500 from Verizon DSL).

---

