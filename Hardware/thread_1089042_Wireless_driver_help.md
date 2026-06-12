---
title: "Wireless driver help?"
date: 2009-03-06
forum: Hardware
---

### Post by mr_biglz0rth1985 on 2009-03-06
I have an HP dv6707 
with an atheros wireless card
the driver it came with was the AR5009 and am trying to get it to operate correctly.
I have a 64 bit system and have 2 GB RAM  memory 
I downloaded ubuntu through WUBI and the release of ubuntu I have is Intrepid IBEX
I'm very new to this and would love to be able to use ubuntu to its fullest capacities.....
I just don't know where to go from here....please help :(
:o
the Wired connection works just fine I'm actually using my Ubuntu OS to post this message.

here is the page that my model laptop is on hp's website
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&lang=en&product=3648475](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&lang=en&product=3648475)

---

### Post by ilioscio on 2009-03-06
Could you post the output of ```
ifconfig -a
```

---

### Post by mr_biglz0rth1985 on 2009-03-06
> **ilioscio said:**
> Could you post the output of ```
ifconfig -a
```

uhm......what does that mean? where do i find output?

---

### Post by ilioscio on 2009-03-06
Ah, of course, sorry for jumping ahead of my self. open up a terminal (Applications > Accessories > Terminal) and then type in ```
ifconfig -a
``` at the blinking cursor and hit enter. It should then output a bunch of text, mine says```
eth0      Link encap:Ethernet  HWaddr 00:19:b9:58:96:db  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:09:4f:97  
          inet addr:192.168.0.87  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe09:4f97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:427738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:533263259 (533.2 MB)  TX bytes:30037490 (30.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-09-4F-97-66-39-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

just go ahead and copy and paste yours here.

---

### Post by mr_biglz0rth1985 on 2009-03-06
> **ilioscio said:**
> Ah, of course, sorry for jumping ahead of my self. open up a terminal (Applications > Accessories > Terminal) and then type in ```
ifconfig -a
``` at the blinking cursor and hit enter. It should then output a bunch of text, mine says```
eth0      Link encap:Ethernet  HWaddr 00:19:b9:58:96:db  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:09:4f:97  
          inet addr:192.168.0.87  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe09:4f97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:427738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:533263259 (533.2 MB)  TX bytes:30037490 (30.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-09-4F-97-66-39-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

just go ahead and copy and paste yours here.

eth0      Link encap:Ethernet  HWaddr 00:1e:68:03:62:a5  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe03:62a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107039615 (107.0 MB)  TX bytes:7573263 (7.5 MB)
          Interrupt:252 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

pan0      Link encap:Ethernet  HWaddr 2a:27:31:df:85:a3  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
thats my ....code? language? that just popped up.... what does that say...? what am i looking for ?

---

### Post by ilioscio on 2009-03-06
eh, it justs tells me a little bit more about the network devices in your computer.

---

### Post by ilioscio on 2009-03-06
alright open a terminal again and this time type in```
sudo gedit /etc/modules
```

this will ask you for your password and then open the file /etc/modules for editing, all you should have to do is add the text ath9k to the end like this
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
ath9k


```

save the file and restart your system, hopefully this will fix your problem.

---

