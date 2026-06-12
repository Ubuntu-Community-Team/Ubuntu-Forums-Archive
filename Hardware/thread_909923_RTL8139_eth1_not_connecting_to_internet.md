---
title: "RTL8139 eth1 not connecting to internet"
date: 2008-09-04
forum: Hardware
---

### Post by thegitksan on 2008-09-04
Good evening folks. I have an Acer Aspire 3610. It comes with an RTL8139/810x ethernet card that works fine in WinXP. I recently acquired a line-of-sight internet connection, which seems to work fine with my Dell desktop.

My Acer is a dual-boot, WinXP and Ubuntu 6.10.

When I plugged the network cable into my laptop, initially, the OS seems to know the connection is there. At that time, it reported limited or no connectivity. I edited the IP (I get a static IP address with my internet access package) to the same settings I use for Windows. I used Networking module as my editor. Upon making the changes, quite suddenly, the OS no longer even recognizes the connection. It sees the card plainly enough. I've checked with IFCONFIG and it reports a card with my IP settings on eth1.

I've tried the following commands I gleaned from another post:
```
sudo modprobe 8139too
ifconfig
sudo dhclient eth1
sudo ifconfig eth1 up
```

The dhclient tries to DISCOVER something, but eventually gives up and tells me it is going to sleep.

Have I missed something really obvious?

---

### Post by eggdeng on 2008-09-04
Can you post
1) the *[I]internal*[/I] IP of your router
2) whether your router is using DHCP
3) the output of ifconfig

---

### Post by thegitksan on 2008-09-05
> **eggdeng said:**
> Can you post
1) the *[I]internal*[/I] IP of your router
2) whether your router is using DHCP
3) the output of ifconfig

Thank you, yes I can reply to all your requests.

1) the IP depends on if I set the Networking to auto or static IP. If I set it for auto (DHCP), then I have no idea what the IP is, nor where I would look for it. If static, then it is as I set it following the Windows example that works: 

192.168.5.27 (UserIP) and 255.255.255.0
192.168.5.254 (Gateway)

I had no idea there could be an internal IP. FYI, I obtain my internet connection via line-of-sight wireless signal, which is picked up by a dish that looks like satellite dish, is amplified and then passed to me via standard RJ-45 cable. It's not satellite, it's broadcast wireless signal.

2) I still don't know if I have a router or not. I can't answer that until I know how to identify a router that may not look like a standard router. I don't think I have a router. I have a tiny box screwed to my wall that sits between my PC and the big dish in my Spruce tree outside. Windows XP uses DHCP in its default mode of connecting and it works fine, however. I have no problem connecting via WinXP, using DHCP as part of the mix.

3) Output of ifconfig follows:

mountainman@athyrium:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0A:E4:E4:DB:E0  
          inet addr:192.168.5.27  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fee4:dbe0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100133 (97.7 KiB)  TX bytes:6335 (6.1 KiB)
          Interrupt:225 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:A4:2D:75:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:b0100000-b0102000 

mountainman@athyrium:~$ 
_______________________

That's the output as most recently generated. I used to have an eth0 definition, and then whilst upgrading from one of the earlier 6.x version to 6.10, I lost eth0 and gained eth1 instead. Not sure if it makes any difference.

I can follow steps if they are clearly laid out. I don't know enough jargon to know all of the basics - I know some, but jargon that only a true command line freak will understand just glazes my eyes. If you have ideas for me to try, please accompany the code for commands with some English to help me decode what the action is and what it is intended to accomplish. I'm not a computer illiterate, I just don't know much linux jargon.

Thanks for any assistance you might be able to offer.

Best regards,
Russell in Canada

---

### Post by eggdeng on 2008-09-05
It looks like the internal IP of your router is 192.168.5.254. Can you try to ping the router. This just means sending a packet of data to see whether the remote machine recieves and returns it - so you know if the connection is open. Open a terminal and type
```
ping 192.168.5.254
```
and then press Intro. If the ping fails, try
```
ping 127.0.0.1
```
which checks the networking stack on your local machine. If you get a result on the first ping above, then try to ping google
```
ping 66.249.91.99
``` or yahoo
```
ping 87.248.113.14
```
Let me know how you get on.

---

### Post by thegitksan on 2008-09-06
Actually, when I try them all, every one of them pings back positive, so I am at least live that far. I can also use traceroute, and the rest of the standard Linux Network Tools that come packaged with Ubuntu.

So.

I have a live connection, but some piece of software is bunging up the works, right? Where do I look next?

---

### Post by eggdeng on 2008-09-06
> Have I missed something really obvious? 
I think both of us have. Go to System -> Administration -> Networking, DNS tab. Make sure you have added the IP of your DNS Server. (If you don't know it, you can get it from the W*nd*ws partitipn by going to the networking device and choosing TCP/IP -> Properties). You might have to restart the interface.
```
sudo ifdown eth1
```
```
sudo ifup eth1
```
and you should be good to go.

---

### Post by thegitksan on 2008-09-07
Good guess, mate, but negatory. I did check the DNS IPs again, though I had already set them as per my Windows successful login. They are indeed set.

I ran the "sudo ifdown" etc. codes and nada. They ran, and did not exhibit any error codes  that I could see on exiting, so I assume they ran as per spec.

Hang on, I'll try restarting and see what that gives after trying those two commands... Nope. nada. Trying a cold boot, with total power off, in case the NIC carries settings in its warm memory... hang on ... 

What's odd is that originally, the OS plainly saw the card and the connection on boot-up. It reported it had low or nil connectivity, which I have learned to cope with in umpteen hotel rooms by setting things like IP. Also, when I originally began setting the laptop up, I also included setting up the Windows side of it all. Originally, Windows didn't connect eitherm, though it also saw the card and was aware of the connection. I set the IP and the DNS there and it just suddenly worked.

Is it possible the card somehow holds in its memory the Windows connection, and thus excludes the Lunix potential?

Okay, just also tried setting it to DHCP (auto detect everything) and it responded to sudo ifdown etc differently. Also to sudo ifup as well. In both cases, it said the network was unreachable. When I tested using the same ping addresses you suggested above, it also said the network was unreachable. So clearly, it needs for the IP address to be hardwired as a static IP number.

I know there's something I am missing. Some vagrant memory is niggling at me, saying, "fix XYZ". What that is, I can't remember. Any more ideas?

Okay, I just reset things back to static IP, and pinged my own fledgling website (incomplete), [www.athyrium.ca](www.athyrium.ca), and it plainly recognized that as well, so I know it is aware of the connection using static IP.

Best,
Russell

---

### Post by eggdeng on 2008-09-07
Are you able to ping domain names, as in
```
ping www.google.com
```
If so, the problem just might be with the browser connection settings. Check in Firefox -> Edit -> Preferences -> Network -> Connection -> Settings
It should be set to Use System Proxy Settings.

If it isn't added already, try adding the DNS manually to /etc/resolv.conf. 
```
sudo gedit /etc/resolv.conf
```
Add the line
```
nameserver 162.42.23.124
```
where 162.42.23.124 is your DNS IP, & restart the interface.

---

### Post by thegitksan on 2008-09-07
Okay, not sure what happened, but it is suddenly working properly. I think. The network icon at top right of my screen still reads as if there is no network available, and yet here I am typing this elated reply to you.

One thing that has changed is that Firefox thinks it is not possible to check for updates, and so that option is greyed out. Weird. Still, something you suggested must have worked, so thanks very much for your help!

---

