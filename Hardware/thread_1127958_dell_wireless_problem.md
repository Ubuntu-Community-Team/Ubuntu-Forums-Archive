---
title: "dell wireless problem"
date: 2009-04-17
forum: Hardware
---

### Post by matt1987 on 2009-04-17
hello i have a dell inspiron e1505 with a 1390 wireless card. i installed broadcom STA drivers for it using the hardware drivers app. it detects and connects to wireless networks fine, but it won't transfer any data. i'm not sure what the problem is. could anyone help? i'm using ubuntu 8.10.

---

### Post by jbrown96 on 2009-04-17
Let's do some testing to figure out how "connected" you are.

Post the output of the following commands

Get detailed hardware info (this is case sensitive)
```
lspci | grep Network
```

System info
```
uname -a
```

Network info
```
ifconfig
```
```
iwconfig
```

Try to connect to some servers
```
ping -c 5 google.com
```
```
ping -c 5 192.168.1.1
``` If the previous command didn't work, then try ```
ping -c 5 10.0.0.0
```

---

### Post by matt1987 on 2009-04-17
```
matt@matt-laptop:~$ lspci | grep Network
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

matt@matt-laptop:~$ uname -a
Linux matt-laptop 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux

matt@matt-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:0b:35:89  
          inet addr:99.179.98.168  Bcast:99.179.98.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe0b:3589/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:153400 errors:1 dropped:1 overruns:0 frame:0
          TX packets:87181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:132052847 (132.0 MB)  TX bytes:6803041 (6.8 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:21:0d:6a  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe21:d6a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1381166 (1.3 MB)  TX bytes:14410 (14.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CF-21-0D-6A-64-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Eastside Farm"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:DF:E2:7F:FF   
          Bit Rate=9 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=55/100  Signal level:-76 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



ping test #1 failed ping #2 and 3 went thru.

---

### Post by jbrown96 on 2009-04-17
You seem to have two internet connections: an ethernet and wireless active.

You are getting an ip address on your wireless connection, so you were right in saying that you're connected, but it's difficult to say what's going wrong.

If you don't mind, what's your network setup? You're getting a public IP address on eth0 (ethernet) 99.179.98.168. This isn't very unusual, but it is strange to have a private ip on wlan0 (wireless 192.168.2.2. That's also strange to have that address instead of 192.168.1.2. 

Here's a test to run, but you need to install some software first.
```
sudo apt-get install nmap
```
Unplug your ethernet connection.
```
sudo nmap -sP 192.168.*.*
```

I think that this is a router problem, not an issue with ubuntu. If the 2nd and 3rd ping tests succeeded (don't know how the third worked?), then you can communicate with the local network, just not the internet.

---

### Post by matt1987 on 2009-04-17
yeah i have 2 active connections. right now i'm using my dsl cable. my wifi comes from a 24 hr restaurant next to me. the strange thing is the wifi signal is from 60%-100% usually. i'll run the tests tommow. i'm off to bed. i appreciate for your help!!

EDIT: never mind i decided to try it. i installed the program and ran the command and it just hung at the start text.

---

### Post by jbrown96 on 2009-04-17
> **matt1987 said:**
> yeah i have 2 active connections. right now i'm using my dsl cable. my wifi comes from a 24 hr restaurant next to me. the strange thing is the wifi signal is from 60%-100% usually. i'll run the tests tommow. i'm off to bed. i appreciate for your help!!

EDIT: never mind i decided to try it. i installed the program and ran the command and it just hung at the start text.

It will take a while to run. There are 256^2 possible addresses to check.

---

### Post by matt1987 on 2009-04-18
ok i got it working. must of been on the server side like you said. thanks for the assistance.

---

