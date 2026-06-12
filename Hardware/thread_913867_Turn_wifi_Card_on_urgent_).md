---
title: "Turn wifi Card on urgent :)"
date: 2008-09-08
forum: Hardware
---

### Post by ozanamn on 2008-09-08
Hi all

I have a 2200bg intel Wireless card. It isn't turned on and i dont know how to. i search loads of forums for ages and tried loads of things. 

Iv tired installing XP on virtualbox and turn the card on but it didnt work because for windows to see it in virtualbox ubuntu had to have turned it on itself, bummer!!!

There is a command line code thats ment to activate it but that does nothing. 

Is there and Hardware programs out there for ubuntu that will turn it on or is there an Device manager like is m$ for ubuntu.


Any help will be much appreciated. Thanks all for your time,

Regards,
Oz

---

### Post by starcannon on 2008-09-08
Lets try the simple option first, forgive me if you already tried.

System>Administration>Hardware Drivers

is your wireless device listed? if so is it enabled with a checkbox next to it?

GL

---

### Post by ozanamn on 2008-09-08
Hi

Haha you no I actually havent I didnt think you could change setting in there thought it was just a view of the hardware. Which it can see it. I cant do it right now but will do it when i get home tonight. Thanks for your response. Ill let you know how I get on.

Regards,
Oz

---

### Post by ozanamn on 2008-09-08
No the wireless card is not in the hardware drivers list as it is installed. 


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:c2:e2:fb:48  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:c2ff:fee2:fb48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2142 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2408962 (2.2 MB)  TX bytes:325280 (317.6 KB)
          Interrupt:16 

irda0     Link encap:IrLAP  HWaddr ff:aa:f5:e8  
          UP RUNNING NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86000 (83.9 KB)  TX bytes:86000 (83.9 KB)

vnet0     Link encap:Ethernet  HWaddr 66:c0:77:d8:8a:ea  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::64c0:77ff:fed8:8aea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5956 (5.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:00:4d:56:7e  
          UP BROADCAST MULTICST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Memory:c8400000-c8401000 

just incase that answers anything for anyone!

---

### Post by starcannon on 2008-09-08
Gonna throw some links at you, hopefully these will help:

[http://ubuntuforums.org/showthread.php?t=883106&highlight=2200bg](http://ubuntuforums.org/showthread.php?t=883106&highlight=2200bg)

[http://ubuntuforums.org/showthread.php?t=860565&highlight=2200bg](http://ubuntuforums.org/showthread.php?t=860565&highlight=2200bg)

and an older post, but should work/be informative.

[http://ubuntuforums.org/showthread.php?t=309041](http://ubuntuforums.org/showthread.php?t=309041)

GL, and have fun.

---

