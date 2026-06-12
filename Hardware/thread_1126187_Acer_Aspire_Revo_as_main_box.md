---
title: "Acer Aspire Revo as main box"
date: 2009-04-15
forum: Hardware
---

### Post by graabein on 2009-04-15
[Acer Aspire Revo listed for pre-order in UK with May 18th release date]("http://www.engadget.com/2009/04/13/acer-aspire-revo-now-up-for-pre-order-in-uk-with-may-18th-releas/")

My comp is an old Pentium4 2 GHz (single core) with 1 GB ram and a GeForce 6600 GT graphics card. I use it for playing [City Of Heroes]("http://en.wikipedia.org/wiki/City_Of_Heroes") (see specs), playing music (Spotify) and video (VLC). It runs with the latest Ubuntu and Windows XP on a 1600x1200 monitor and an old crappy television set (tv-out).

Does the Revo meet my requirements? It would be sweet to go for a small low priced box instead of building a new machine from the ground up. I have my data on external storage so no problem with hd space.

I'm not that into hardware, processors n stuff. Any help and advice would be greatly appreciated!

---

### Post by ulgor on 2009-04-21
**The short answer to your question: **
Yes, this should be enough for the use-cases you described.

I do not own a nettop or netbook, but that's my opinion. This Nettop will have decent graphics, with at least the same processor power as your old P4. More importantly, it has MUCH better energy efficiency, which also means less cooling and less fan noise (or none at all). Personally, I also like the small size and design ;)
edit: I am not sure about the speed of your 6600 GT. Being a dedicated graphics card for desktop boxes, it might be faster than the 9400M, which is designed for mobile devices. The 9400 is a very good chip, but I am not 100% sure how it compares to a 6600GT, especially at higher resolutions.


**The long answer:**
The Acer Revo uses an Atom 230 and the new Nvidia 9400M graphics:

The Atom 1.6GHz processor is comparable to a 1.2GHz Celeron, which is not very fast, even compared to other single core processors. Do not expect the Atom to be a Core Duo... but its definitely as good as an old P4.

The 9400M graphics actually seems to be one of the best integrated graphics out there, you can even play games with it - sure, maybe only at 1024*768 at 25 frames, but thats a LOT more than ANY other integrated chip can handle! The new MacBook also uses 9400M, which is definitely a very good sign!

The combination of these two means that every application that takes advantage of the graphics chip will be fine; i.e. decoding HD videos can (usually) be done by the GPU, something the Atom alone could not do. Applications that need a lot of processor power will suffer.

---

### Post by visik7 on 2009-05-20
I use aspire revo with xbmc on full hd tv watching full hd movies thanks to nvidia ion and vdpau support it's AMAZING

---

### Post by karl98 on 2009-05-22
Hi,

I'd really like to buy this Acer Aspire Revo, Do you know if the last Ubuntu can run on this machine, are the drivers developped?  I think the Aspire Revo will be available in France about the 6 th of June, and it comes with windows vista....so I have to find an alternative.
I would like to use this machine both as media center and  web / ftp server .


Thanks

---

### Post by stanabe on 2009-06-15
Just found:
How to install Ubuntu and Boxee on the Acer Aspire Revo
[http://www.greenhughes.com/content/how-install-ubuntu-and-boxee-acer-aspire-revo]("http://www.greenhughes.com/content/how-install-ubuntu-and-boxee-acer-aspire-revo")

---

### Post by deeptingler on 2009-08-05
have just bought a Revo and loved Ubuntu for years now and first thing to install..... great experience so far... had to search for drivers but 20 mins later up and running and loving the silence

---

### Post by vish_revo on 2009-08-08
> **deeptingler said:**
> have just bought a Revo and loved Ubuntu for years now and first thing to install..... great experience so far... had to search for drivers but 20 mins later up and running and loving the silence


I guess you're very lucky being able to find all the drivers in such a time, I've been looking for MCP79 Ethernet drivers to get the Wire LAN working but having no luck.
Can anyone help me out on this issue?

ps there are no lights showing on the network card, and the wireless is working perfectly and able to connect to the same router. 


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:68:64:73:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1752 (1.7 KB)  TX bytes:1752 (1.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:54:ab:31  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe54:ab31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30835048 (30.8 MB)  TX bytes:2235679 (2.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-54-AB-31-62-33-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by ytene on 2009-09-10
I am interested by your posts. I have had a Revo for a few months now, and I got wired network up and running automatically on the first installation. I am running 9.04 Junty, AMD64 distribution [works fine]. Using the LiveCD on another machine I created a bootable USB Memory Stick installer and went from there.

There are rare moments of sluggish performance, but on the whole this little thing works really, really well, even though it's only got a 1.6GHz Atom processor. [ OK, I did cheat *slightly* and upgraded to 4Gb of RAM, but that won't make *that* much difference. 

Today I've just taken delivery of a Dell 24" Ultrasharp Monitor [ 1920x1200 resolution ]. The monitor via which I installed Jaunty to the Revo was a Samsung 214T, a 21.4" unit with 1600x1200 resolution. 

For reasons currently eluding me, I am not able to upgrade the configuration of my machine to operate at 1920x1200, even though the nVidia documentation for the 9400m chipset suggests this is entirely possible. Ah well, back to Google for me then...

Here's my current networking config. Let me know if you need any more help with this...

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:68:62:dc:04  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:68ff:fe62:dc04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7419 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6928940 (6.9 MB)  TX bytes:1070661 (1.0 MB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22693 (22.6 KB)  TX bytes:22693 (22.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:23:8f:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-23-8F-76-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by ksimonov on 2009-10-02
I have the problem with wired LAN port too. ifconfig says that interface eth0 isn't configured. And even led on port doesn't blinking when cabel is plugged in. Looks like integrated network card is totally disabled or dead. May be it must be enabled somewhere in the BIOS?

---

### Post by loraul on 2009-10-14
> **ksimonov said:**
> I have the problem with wired LAN port too. ifconfig says that interface eth0 isn't configured. And even led on port doesn't blinking when cabel is plugged in. Looks like integrated network card is totally disabled or dead. May be it must be enabled somewhere in the BIOS?

Hello,
   I have the same problem. Are you resolve it?

Thanks.

I have the solution:

[http://www.greenhughes.com/content/how-install-ubuntu-and-boxee-acer-aspire-revo#comment-994](http://www.greenhughes.com/content/how-install-ubuntu-and-boxee-acer-aspire-revo#comment-994)

---

