---
title: "Check the hardware."
date: 2010-01-11
forum: Hardware
---

### Post by supernova42 on 2010-01-11
I am running Ubuntu 9.10 and I and working wirelessly through an attachable wireless router to which i lost the box so I do not know the name or have the driver CD (for my second windows portion).  Is there a way to find out the name of the the hardware.

---

### Post by windoze87 on 2010-01-11
er...you need to know what the router is? maybe a sticker on the bottom of the router? If not type 192.168.2.1 into any browser and hit enter, that'll give you all kinds of information, including brand and model number.

---

### Post by scytherswings on 2010-01-11
Well, I know that MAC addresses are manufacturer specific... or at least I have read... If you can find out the MAC address of your device it may help narrow down your search.. Although honestly the easiest thing to do is to pick up the device, and flip it over and start reading :)

Well 192.168.2.1 may not be his router's specific ip address. He needs to find his DHCP server's address which could be at that address, but it may not be. I would also try 192.168.0.1, 192.168.1.1, 192.168.0.254 and 192.168.1.254 if you don't now it. I know there are more, but from my experience, those have been the most common. Hope that helps.

---

### Post by gabo.cr on 2010-01-11
You can plug the computer to the router with the network cable and on Terminal type:

```
ifconfig
```

That will give you the IP address of the router, paste that on the browser and you will see the model of you router.

---

### Post by scytherswings on 2010-01-11
> **gabo.cr said:**
> You can plug the computer to the router with the network cable and on Terminal type:

```
ifconfig
```That will give you the IP address of the router, paste that on the browser and you will see the model of you router.

That's an even better idea that what I posted.. do what he said hahaha. Can't believe I didn't think of that, lol long day... And using Windows too much has corrupted my brain... sadface

---

### Post by supernova42 on 2010-01-11
now how do I find that from this
```
eth0      Link encap:Ethernet  HWaddr 00:1a:92:41:1f:90  
          UP BROADCAST ALLMULTI MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2735 (2.7 KB)  TX bytes:2735 (2.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:13:ac:09  
          inet addr:10.0.1.10  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe13:ac09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8002565 (8.0 MB)  TX bytes:730879 (730.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-13-AC-09-31-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by scytherswings on 2010-01-11
If I'm correct (forecast of 50% chance today) then I think the address of your router is 10.0.1.10 unless that's your address, Its been a while since I've looked at that output, but either way, I'd type it into a web browser and see where it takes you. No Http:// or any .com's just the address itself. Hope that helps.

---

### Post by supernova42 on 2010-01-11
I tried that and got the
"Firefox can't establish a connection to the server at 10.0.1.10." error
Any other thoughts?

---

### Post by Marvin666 on 2010-01-11
I looked at my ifconfig, and the router ip wasn't listed.
198.162.1.1 worked on every router I tired.

---

### Post by supernova42 on 2010-01-11
I am the biggest idiot ever.  I said wireless router but what I am actually trying to find out is my wireless adapter?  Sorry about that.

---

### Post by supernova42 on 2010-01-12
Anyone?

---

### Post by gabo.cr on 2010-01-12
Type this in Terminal:

```
lspci -v | less
```

If you have a USB adapter type this:

```
lsusb
```

I hope that helps.

---

