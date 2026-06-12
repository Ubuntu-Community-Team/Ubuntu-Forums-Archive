---
title: "[SOLVED] Help with ssh-- port 22 connection refused"
date: 2008-09-01
forum: General Help
---

### Post by Iceman99one on 2008-09-01
I am new to using ssh and wanted to try it out. I have been trying to connect to my ubuntu machine from my mac using ssh. I keep getting this error message:

```

$ ssh 127.0.0.1
ssh: connect to host 127.0.0.1 port 22: Connection refused

```

Any ideas or suggestions are much appreciated!

Thanks!

---

### Post by cdtech on 2008-09-01
> ssh 127.0.0.1
That's your local, you'll need the IP for your Ubuntu machine

---

### Post by Iceman99one on 2008-09-01
> **cdtech said:**
> That's your local, you'll need the IP for your Ubuntu machine

What do you mean by "local"? I thought that was the IP from my ubuntu machine. 

Thanks for the quick response!

---

### Post by mellowd on 2008-09-01
> **Iceman99one said:**
> What do you mean by "local"? I thought that was the IP from my ubuntu machine. 

Thanks for the quick response!

local is your current PC. 127.0.0.1 refers to itelf

::1 is the ipv6 version of localhost

---

### Post by Iceman99one on 2008-09-01
In what range would the IP be that I'm looking for?

---

### Post by mellowd on 2008-09-01
> **Iceman99one said:**
> In what range would the IP be that I'm looking for?

No idea, it could be anything from 1.0.0.1 - 238.255.255.255

check your linux box by typing: 

ifconfig

What are the results, we should be able to get it from there.

---

### Post by Iceman99one on 2008-09-01
Here are my results from ifconfig:

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:ad:d0:37:ce  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::280:adff:fed0:37ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8711155 (8.3 MB)  TX bytes:414850 (405.1 KB)
          Interrupt:16 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112100 (109.4 KB)  TX bytes:112100 (109.4 KB)

```

---

### Post by mellowd on 2008-09-01
This is the IP address you need: 192.168.0.102

---

### Post by Iceman99one on 2008-09-01
Here is what I get when I do ssh 192.168.0.102:

```

$ ssh 192.168.0.102
6holland@192.168.0.102's password:

```


This was not exactly what I was expecting. 6holland is my username on my mac. And any password I can think of does nothing but this:

```

Permission denied, please try again.

```

Any thoughts?

---

### Post by cdtech on 2008-09-01
The ifconfig you gave above was from your mac?
Did you give the ifconfig from a terminal on the Ubuntu machine?

---

### Post by Iceman99one on 2008-09-01
The ifconfig I gave was from my ubuntu machine.

Here is the one from my mac:

```

$ ifconfig
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
	inet 127.0.0.1 netmask 0xff000000 
	inet6 ::1 prefixlen 128 
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 00:1b:63:b9:1e:b2 
	media: autoselect status: inactive
	supported media: autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 10baseT/UTP <full-duplex,flow-control> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback> 100baseTX <full-duplex,flow-control> 1000baseT <full-duplex> 1000baseT <full-duplex,hw-loopback> 1000baseT <full-duplex,flow-control> none
en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	inet6 fe80::21c:b3ff:fe74:2285%en1 prefixlen 64 scopeid 0x5 
	inet 192.168.0.100 netmask 0xffffff00 broadcast 192.168.0.255
	ether 00:1c:b3:74:22:85 
	media: autoselect status: active
	supported media: autoselect
fw0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 4078
	lladdr 00:1e:52:ff:fe:40:2a:2a 
	media: autoselect <full-duplex> status: inactive
	supported media: autoselect <full-duplex>

```

---

### Post by monkeyking on 2008-09-01
I don't think a ssh server is installed per default.
You should install that also.

---

### Post by cdtech on 2008-09-01
> **monkeyking said:**
> I don't think a ssh server is installed per default.
You should install that also.

I'm thinking the same thing monkeyking.....
```
sudo apt-get install openssh-server openssh-client
```

Have you tried, from the Ubuntu machine:
```
ssh localhost
```

---

### Post by Iceman99one on 2008-09-01
I have an ssh server installed on my ubuntu machine, but I'm not sure how it is configured.

I have aready done:

```

sudo apt-get install openssh-server openssh-client

```

---

### Post by mellowd on 2008-09-01
> **Iceman99one said:**
> I have an ssh server installed on my ubuntu machine. But I'm not sure how it is configured.

Try ssh'ing to it from the linux box itself. 

ssh 127.0.0.1

---

### Post by cdtech on 2008-09-01
I see......
> $ ssh 192.168.0.102
6holland@192.168.0.102's password:
This is correct. You just need to set up your OpenSSH keys.

---

### Post by Iceman99one on 2008-09-01
Logging in using ssh directly from my ubuntu machine worked fine.

---

### Post by Iceman99one on 2008-09-01
> **cdtech said:**
> I see......

This is correct. You just need to set up your OpenSSH keys.

How would I set up my openssh keys?

---

### Post by cdtech on 2008-09-01
Whats your user name on the Ubuntu box?
Try $ ssh username@192.168.0.102

---

### Post by Iceman99one on 2008-09-01
> **cdtech said:**
> Whats your user name on the Ubuntu box?
Try $ ssh username@192.168.0.102

I tried $ ssh username@192.168.0.102 and it worked! I was able to log in.

Thank you everyone for all your help!

Much appreciated!

---

### Post by cdtech on 2008-09-01
Awesome. Good luck....

---

### Post by divyabdasar on 2010-09-13
Even i had same problem when i tried to connect to another machine 

ssh deepu@192.168.1.***

error:

ssh: connect to host 192.168.1.*** port 22: Connection refused

After two hours google found out that , machine i was trying to connect ssh server wasn't properly installed.

Cheers ;):p:D

---

