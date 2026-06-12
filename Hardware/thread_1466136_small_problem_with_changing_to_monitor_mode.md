---
title: "small problem with changing to monitor mode"
date: 2010-04-30
forum: Hardware
---

### Post by adoBo on 2010-04-30
hello everyone :P

i have been trying to set my Acer Aspire One (netbook) into monitor mode with iwconfig for about an hour, but have been unsuccessful.

this is what i am typing into the terminal



root@Logos:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:5a:54:5d:64  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:7c:8d:00  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe7c:8d00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:70304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:88392034 (88.3 MB)  TX bytes:5268966 (5.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-7C-8D-00-37-63-00-00-00-00-00-00-00-00  
          UP NOTRAILERS RUNNING PROMISC ALLMULTI  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@Logos:~# ifconfig wmaster0 up
root@Logos:~# iwconfig wmaster 0 mode monitor
iwconfig: unknown command "0"
root@Logos:~# iwconfig wmaster0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wmaster0 ; Operation not supported.



at this point, obviously i am stuck. is there a way around this speed bump?

-thanks

---

### Post by Fafler on 2010-04-30
Make sure your interface actually supports monitor mode. Not all wifi chips are capaple of that.

---

### Post by adoBo on 2010-04-30
is there some other method that i could try to get around this?

---

### Post by adoBo on 2010-05-11
for those who are trying this and getting the same error try this

:~# iwconfig

      **you are looking for a wireless extension (mine is wlan0)**

:~# airmon-ng start wlan0


Interface	Chipset		Driver

wlan0		Atheros 	ath5k - [phy0]
				(monitor mode enabled on mon0)

      **you may get a few errors, dont worry about them**

viola! you now have a device that you can use to use monitor mode :)

---

