---
title: "Ubuntu 10.10rc Linksys wusb54gc v3 rt2870 chip"
date: 2010-10-02
forum: Hardware
---

### Post by fallen0127 on 2010-10-02
This is the first release from Ubuntu that has natively recognised my usb wireless card. However, after about a minute of working it slows to a crawl and disconnects. Then it starts an endless loop of trying to connect and failing. Any help would be appreciated. Here is my ifconfig, and lsusb outputs
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:11:d8:8e:e3:ec  
          inet addr:192.168.15.3  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe8e:e3ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:81052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109464585 (109.4 MB)  TX bytes:4230129 (4.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:69:71:f0:c4  
          inet6 addr: fe80::223:69ff:fe71:f0c4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8768086 (8.7 MB)  TX bytes:445394 (445.3 KB)

```
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0d62:001c Darfon Electronics Corp. Benq X120 Internet Keyboard Pro
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 003: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0d62:001c Darfon Electronics Corp. Benq X120 Internet Keyboard Pro
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1737:0077 Linksys WUSB54GC v3 802.11g Adapter [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by fallen0127 on 2010-10-03
Hmmmm.... same friendly replies I have come accustomed to here at the Ubuntu forums!!! Anyway, not sure what I did, but after hours of trying things, I gave up last night without it working. I woke up this morning booted the comp, and it works. Thanks anyway.

---

### Post by Dapman01 on 2010-10-12
Having this same problem
does anyone know how to fix it?

---

### Post by alfiegee on 2010-11-01
I'm also having the same problem. It sucks and makes me hate my computer even more.

---

### Post by brian2554 on 2010-11-04
Likewise, I am in the same proverbial "boat"..."please OBI-WAN, you are my only hope"

:) Hope is all I've got in the way of finding a solution short of purchasing another wifi dongle.

---

### Post by infernowolf36 on 2010-11-22
i can't even get the system to recognize my usb adapter. i'm a bit rusty on my ubuntu, plus the newest has some new stuff and a new feel to it. last version i had was 9.10 a while ago. any advice on simply getting it to recognize or acknowledge the usb adapter would be appreciated. wusb54gc

---

### Post by Goolie on 2010-12-06
> **infernowolf36 said:**
> i can't even get the system to recognize my usb adapter. i'm a bit rusty on my ubuntu, plus the newest has some new stuff and a new feel to it. last version i had was 9.10 a while ago. any advice on simply getting it to recognize or acknowledge the usb adapter would be appreciated. wusb54gc

Check out ndiswrapper, it'll let you utilize the windows driver for this and other wireless drivers.  I had to use it to have the device recognized, but like many others, it seems that it just loses connection and fails to reconnect.

---

### Post by TBABill on 2010-12-06
Can you try: ```
sudo gedit /etc/modprobe.d/blacklist.conf
``` and add the following lines to the end of the file: ```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
```
 
Then the following:
```
sudo gedit /etc/modules
```
and at the end of the file add
```
rt2870
rt2870sta
```
 
Then restart. If it still does not start on its own, then ```
sudo modprobe rt2870sta
```

---

### Post by akolahi on 2010-12-20
Thanks [TBABill]("http://ubuntuforums.org/member.php?u=974469"),

appears to have worked for me :D

---

### Post by dithan on 2010-12-26
Thanks TBABill this seems to have worked for me too.

Nice easy directions for someone who's never touched linux before today. 

Thanks again.

---

### Post by tora201 on 2011-04-02
Sorry for reviving an old post. Good instructions, although they don't quite appear to working for me. After following this guide, it now does try to connect upon boot, but the wheel just spins and then after a minute stops and says "Wireless Network - You are not disconnected."

Any other ideas? Thanks.

---

### Post by infernowolf36 on 2011-04-03
that sounds silly. I have no idea on what that would mean but I'm just letting you know that someone heard you. :) 

Does it show any available networks?

---

### Post by en4ian on 2011-04-03
I have the same trouble and am unsure what to do. My internet will work okay for a good 10 minutes or so and then it will disconnect. I have to replug the USB adapter to get it working again.

I am afraid to try the blacklist suggestion a few posts back. What exactly does that do?

---

### Post by infernowolf36 on 2011-04-03
En4ian:

blacklisting (as far as blacklisting goes) is basically blocking something from accessing or controlling something. generally the blacklisting included in this thread would block any potential conflicting actions between scripts. it's possible that since you can connect but not stay connected (and you're sure it's the adapter) that the problem might be with some software telling it to do one thing then another thing at the same time causing a sort of gridlock. blacklisting would simply block that from happening. feel free to try it and remember that you can reverse it by simply undoing whatever it is that you did.

---

### Post by tora201 on 2011-04-04
Hey mate, thanks so much. Yes, it shows networks. The thing is they connect fine to my laptop, just not using the USB adapter. No idea what that means. I have tried various blacklisting, etc from other threads but it makes no difference. And, does not matter what kind of security/or even no security. The same result: the wheel spins for about a minute or two, then I get the message, "disconnected."

---

### Post by infernowolf36 on 2011-04-04
i'm not sure if there ever was a fix for this.. hopefully someone with more knowledge will come along. i dont have much else to help with on that note. i'm sure you already tried using ndiswrapper and enabling broadam right?

---

### Post by TBABill on 2011-04-04
The important things are:
 
1. /etc/modules is a file that lists drivers set to enable on startup
2. /etc/modprobe.d/blacklist.conf lists drivers set to NOT be enabled on startup (blocked). You can play with this file by adding a blacklist line, saving and restarting, then just removing it and restarting again to restore back to where it was. You won't harm your system blacklisting a driver.
3. Look in /etc/modules for Ralink devices to make sure you don't have more than one driver trying to drive the same device (just like 2 people can't drive one car). Conflicts create disconnects, situations where you cannot connect, etc.
4. The command "lsmod" (LSMOD without quotes) will list all system drivers currently in use. 
 
I have fought a few Ralink devices and most problems revolve around these things. There are certainly other issues to be found as well, but common ones are conflicts, missing drivers, missing firmware, etc.
 
It's usually best to start your own thread with a problem than tag onto someone else's. It makes helping you out much more difficult when more than one person is posting their issue, hardware, getting advice, etc.

---

