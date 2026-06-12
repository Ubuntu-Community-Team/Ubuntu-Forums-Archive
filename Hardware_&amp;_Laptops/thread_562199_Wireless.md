---
title: "Wireless"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by Edwin Eveningfall on 2007-09-28
Hi everybody!

I have installed 2 weeks ago Ubuntu Feisty and i'm really satisfied!

I have an Asus laptop a2826suh, and i have a problem:

my wi-fi is always turned on ( since there is always the light of on the board of the notebook ) and i can't find a way to turn it off!
i have already disabled the wi-fi connection ( from the menu near the clock ) but the device is always active and it causes me lots of headaches!
In windows i used to disable the wi-fi card  simply from hardware manager ( the light on the board used to turn off ) and i active it only when i needed it ( the same i did for the IRDA ).

can somebody help me with this quest?

Thanks!

---

### Post by eggdeng on 2007-09-28
Assuming your wireless  device is wlan0 (you can check this by typing ifconfig in a terminal), you should be able to disable it with ```
sudo ifdown wlan0
``` ```
sudo ifup wlan0
``` will start it again.

---

### Post by Edwin Eveningfall on 2007-09-28
this is what i have

andrea@andrea-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:88:C3:7E  
          inet addr:192.168.0.141  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe88:c37e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:204004 (199.2 KiB)  TX bytes:48067 (46.9 KiB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

and then

andrea@andrea-laptop:~$ sudo ifdown wlan0
Password:
ifdown: interface wlan0 not configured


what does this mean? sorry if i'm not so expert...

---

### Post by eggdeng on 2007-09-28
wlan0 and eth0 are names the system gives to network interfaces. wlan0 is usually the wireless & eth0 the (wired) ethernet card. 
You seem to have only one active interface - eth0, so this is presumably your wireless. So just type ```
sudo ifdown eth0
``` and ```
sudo ifup eth0
``` to bring it back up.

---

### Post by Edwin Eveningfall on 2007-09-28
I tried to use your code in the terminal but the light is always on and then it reconnects by his ownself after a few seconds.

---

### Post by Edwin Eveningfall on 2007-09-28
andrea@andrea-laptop:~$ sudo ifdown lo
ifdown: interface lo not configured
andrea@andrea-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:88:C3:7E  
          inet addr:192.168.0.141  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe88:c37e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:273518 (267.1 KiB)  TX bytes:44428 (43.3 KiB)
          Interrupt:21 Base address:0xa000 

andrea@andrea-laptop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 5215
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:88:c3:7e
Sending on   LPF/eth0/00:11:2f:88:c3:7e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
andrea@andrea-laptop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 5746
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:88:c3:7e
Sending on   LPF/eth0/00:11:2f:88:c3:7e
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.141 -- renewal in 298 seconds.
andrea@andrea-laptop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
andrea@andrea-laptop:~$ sudo ifdown lo
ifdown: interface lo not configured

---

### Post by Edwin Eveningfall on 2007-09-29
Can someone help me with the code? I don't understand its meaning...
The code only disables the connection but not the device which remains always on...

---

### Post by jpyanowski on 2007-09-29
"In windows i used to disable the wi-fi card  simply from hardware manager ( the light on the board used to turn off ) and i active it only when i needed it"

So I take it there is no switch to turn off your wireless  card? If you disable your wireless interface it is just the same as turning off the card. I'm confused. :confused:

---

### Post by Edwin Eveningfall on 2007-09-30
sorry if i answer only now but i'm from a far far away part of the world :-).

No i have no switch on the laptop. In windows when i disabled the device the light turned off so, probably, that meant that there was no electricity there.

In ubuntu when i disable the wireless i think it disables only the wi-fi connection and not the wi-fi device.

Does this make sense?

---

### Post by Edwin Eveningfall on 2007-10-01
???

---

