---
title: "HP DV6500, Broadcom connects, internet cuts out after 10 mins"
date: 2008-09-17
forum: Hardware
---

### Post by ibtuten on 2008-09-17
Copied from another forum I frequent...

Problem description: Ok, so I installed Ubuntu 8.04 on my HP DV6500 laptop. Everything went smoothly, and it even recognized that I needed restricted packages for my nVidia driver and my Broadcom wireless driver. After installing those and restarting, everything on the laptop works flawlessly, except that the wireless drops out after 10 minutes or so. The GUI wifi indicator still shows me having a signal, and iwconfig lists my network as being the one connected to, but there's no internet, and pinging 192.168.1.1 (my router) doesn't return anything.

Attempted fixes: I have tried manually setting up my wifi using ifconfig and/or the gui tools, but that doesn't connect in the first place, even using the same values that ifconfig/iwconfig give me when I'm successfully connected. I tried ndiswrapper with the latest Broadcom driver from Open-WRT.org, and couldn't get that working. The connection time is now down to 2 or 3 minutes. Internet works fine for those 2 or 3 minutes, and then it's in the shitter.

Operating system: Ubuntu 8.04

System specs: HP DV6500, Broadcom Wireless

update: ifconfig shows eth0, lo, wlan0, and wmaster0... could wlan and wmaster be conflicting in some way?

update: tried disabling IPv6, that doesn't work. 

update: I read that the nvidia driver and the Broadcom firmware can clash sometimes, but switching "nvidia" to "nv" in my xorg.conf puts me in 2D-only mode, and that is not acceptable :P

```

ibtuten@Mjollnir:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:c6:2f:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2600 (2.5 KB)  TX bytes:2600 (2.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:1a:73:bb  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:193691 (189.1 KB)  TX bytes:37799 (36.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-00-00-1A-73-BB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

ibtuten@Mjollnir:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"[MYNETWORKNAME]"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:39:46:B7:3A   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=76/100  Signal level=-56 dBm  Noise level=-56 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

edit: The plot thickens... in my syslog:
```
Sep 17 19:20:57 Mjollnir kernel: [  579.881674] b43-phy1 ERROR: PHY transmission error
```
And those repeat indefinitely until I reboot. Disabling and re-enabling the network (or merely disconnecting and reconnecting) don't do the trick. It takes a full reboot.

edit2: Ooook... I tried upping the bandwidth to 54M and now the driver doesn't exist in my restricted modules list. Awesome.

---

