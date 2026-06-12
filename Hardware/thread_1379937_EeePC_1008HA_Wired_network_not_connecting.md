---
title: "EeePC 1008HA Wired network not connecting"
date: 2010-01-13
forum: Hardware
---

### Post by karl_eller on 2010-01-13
Not sure if this should be here, or in the UNR board, but here we go :P

I picked up an EeePC 1008HA about a week ago, and pretty much the first thing I did was nuke XP and play around with a couple of Linux variations (Moblin, UNR 9.10). UNR 9.10 worked fine right out of the box. Wireless, Wired, Bluetooth, webcam, the works. Uninstalled UNR 9.10 to try out Windows 7 and update the BIOS (new BIOS improved wifi, apparently) at the same time (little did I know that Asus EZFlash is still included, just hidden, and I ended up using it anyway). Win7 didn't turn out so great after all, so again with the HDD nuking, and back came UNR 9.10. However turns out that the new BIOS did something with booting from USB, so I had to roll back to an earlier BIOS, install UNR 9.10, then re-flash back to the newest version.

So now, Wireless, Bluetooth and web cam still works, however wired network doesn't. Netbook still detects eth0, but when I try to connect to the wired, it goes through the connecting icon animations, and then comes with a "Wired Network: Disconnected" message. eth0 still shows up on the network menu, and the activity lights on the router show up, but it refuses to connect.

I've tried installing the AR81 Family ethernet drivers, and that hasn't changed anything. Tried multiple network cables and router ports, and I've tried connecting directly to the modem, but no luck.

output from ifconfig looks a bit like this:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:58:54:7f  
          inet6 addr: fe80::226:18ff:fe58:547f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:5750 (5.7 KB)  TX bytes:810 (810.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:36:ba:1f  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe36:ba1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43741777 (43.7 MB)  TX bytes:2302004 (2.3 MB)

```

Anyone have any advice as to what I can do to fix this? Wifi connection in my room is a little so-so sometimes, so I want to be able to hook into the wired network every now and then.

---

### Post by barnex on 2010-01-13
It seems like your router did not provide your wired connection with an IP(v4) address. Are you sure eth0 is set to use DHCP ('obtain network address automatically' in network manager)?

---

### Post by karl_eller on 2010-01-13
> **barnex said:**
> It seems like your router did not provide your wired connection with an IP(v4) address. Are you sure eth0 is set to use DHCP ('obtain network address automatically' in network manager)?
Ok, so this is going to sound really stupid, but it turns out that the IPv6 settings were the problem. Previously I had IPv4 set to Automatic (DHCP), and IPv6 set to Automatic, but it was only trying to connect using IPv6 (which I'm guessing my router/modem isn't set up for), and not trying IPv4. I changed IPv6 method to Ignore, and now the wired network works just fine.

Yet another case of me brain-farting on something that should be fairly simple, until someone reminds me about it :P

Eller

---

