---
title: "ifup, ifdown not working"
date: 2008-08-25
forum: General Help
---

### Post by monkeyking on 2008-08-25
hi,
I used to be able to put a interface up and down.
Using

```

ifdown eth0
ifup eth0

```

But now it says

```

ifdown: interface eth0 not configured

```

btw I'm sure my netinterface is eth0

```

eth0      Link encap:Ethernet  HWaddr 00:18:8b:6a:a8:76  
          inet addr:192.38.114.195  Bcast:192.38.114.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe6a:a876/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97665 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32849 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61857885 (58.9 MB)  TX bytes:4110712 (3.9 MB)
          Interrupt:16 

```

The problem is not, that I'm not on the internet,
I just need a commandline command, for putting it up and down.


thanks in advance

---

### Post by oldmanteabags on 2008-08-25
Try

```
ifconfig eth0 down
ifconfig eth0 up
```

---

### Post by nitro_n2o on 2008-08-25
what is the content of /etc/network/interfaces

---

### Post by monkeyking on 2008-08-25
The ifconfig eth0 up/down command works.
But my network goes up immidiatly after I pull it down.
Do anyone have any ideas?


This is my interface file, should I just add eth0, to make everything work?
```

cat /etc/network/interfaces 
auto lo
iface lo inet loopback



```

---

### Post by oldmanteabags on 2008-08-25
confirm the config of eth0, by using
```
ifconfig eth0
```

respwaning eth0, good one.

just some ideas
check wake on lan and deactivate, 
match the hardware to the driver with
```
lspci
```

**EDIT** -- My interface file is the same as yours and my eth0 is working fine. not sure why the eth0 entry is not listed. things sure are changing.

---

### Post by caljohnsmith on 2008-08-25
> **monkeyking said:**
> The ifconfig eth0 up/down command works.
But my network goes up immidiatly after I pull it down.
Do anyone have any ideas?

This is my interface file, should I just add eth0, to make everything work?
```

cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```
Just an FYI, but for ifup/ifdown to work, your interface needs to configured in the /etc/network/interfaces file. From the man page:
> DESCRIPTION
The  ifup  and  ifdown  commands  may be used to configure (or, respec&#8208;tively, deconfigure) network interfaces based on interface  definitions in the file /etc/network/interfaces.
So if you want to use ifup/ifdown, you could put your eth0 interface into /etc/network/interfaces like:
```
iface eth0 inet dhcp
auto eth0
```

---

### Post by monkeyking on 2008-08-25
Thanks, after including my eth0 to /etc/network/interfaces

Everything works as usual

thanks

---

