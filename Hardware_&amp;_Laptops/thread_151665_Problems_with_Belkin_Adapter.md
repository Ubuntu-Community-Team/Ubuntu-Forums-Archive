---
title: "Problems with Belkin Adapter"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by pablo180 on 2006-03-28
I have the Belkin USB F5D5050 Ethernet Adapter, I got everything installed and on the internet fine, but for some reason the adapter only runs at 110K, even when transferring files over the LAN. 

Is there anyway to change the speed of a network adapter? Or does anyone know where I am going wrong?

Thanks for the help.

---

### Post by pablo180 on 2006-03-28
I should add that I have checked the USB port and it is working fine at 12.0MB/s (USB1.1), it picks up the Ethernet Adapter correctly and at the speed of 10/100MB/s but it just seems to work at 110K regardless. 

Does anyone have any idea what could be causing this?

---

### Post by pablo180 on 2006-03-29
OK so being a newbie I have no idea about this and after searching the forums I have found nothing of help, so I am hoping that providing a little more information may be of use.

I entered the command **ifconfig eth0** to check my connection and this is what I received;
 ```

eth0      Link encap:Ethernet  HWaddr 00:05:1B:00:6C:6C
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::205:1bff:fe00:6c6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:251424 (245.5 KiB)  TX bytes:32928 (32.1 KiB)
```

Now I am no expert but I think that those last last two readings;

> RX bytes:251424 (245.5 KiB)  TX bytes:32928 (32.1 KiB)

Should be in MiB for a Ethernet connection right? Anyone have any idea what those readings are or how they can be changed?

---

### Post by roachk71 on 2006-03-29
[LEFT]The two readings in question are the total number of bytes received and transmitted by the device. To find out your link speed and other wireless information, try this:

```
 sudo iwconfig 
``` Also: It looks like you're using the wired ethernet adapter instead of your wireless card, unless you don't have the wired variety installed at all.

In addition, the madwifi driver doesn't support all features of certain cards or dongles.

Another user has an F5D7050uk, and he's having an impossible time getting this one to work...

Please post the information you get from this command, and I'll try to help you further.
[/LEFT]

---

### Post by pablo180 on 2006-03-30
Thanks for the reply, sorry but I don't think that I was very clear in my initial post. 

I don't have a wireless adapter but a Belkin F5D5050 USB to Ethernet 10/100Mbps adapter, basically it plugs into the USB socket and allows me to then attach an Ethernet capable to it and use the internet as Linux picks it up as a Ethernet card.  

It all works fine, in that I have the right drivers, I can get on the net and my home network. The only problem that I have is that my Broadband speed is 1MB and my network speed is 100MB but the laptop with Ubuntu on it seems to only run at 110K, whether on the internet or transfering files across the network. And I have no idea why. 

This is causing me problems as even downloading the Ubuntu updates is going to take me days! And transferrring files to and from the laptop takes ages.

---

### Post by roachk71 on 2006-03-30
Hmm.

I've searched all over the place for answers, even Googling around. According to most of the sites I've visited this adaptor works fine with the Pegasus driver (which I believe is included as a module.)

There may be an overhead issue. If there are other devices attached to the USB controller, they may be using some of that maximum 12Mbps bandwidth (mice, keyboards, printer, etc.)

Some USB controllers limit bandwidth to the slowest device on the bus, as well. Keyboards and mice typically use only 1.5Mbps maximum.

I'm also unfortunate enough to be limited by a USB 1.1 controller (old-ish notebook.) That's why I steer clear of USB networking.

If your computer has a 32-bit cardbus, you might want to check out PC Card network cards instead. These USB dongles are mainly designed for use with USB 2.0.

If, however, you'd like to keep using this adaptor, I suggest using PS/2 keyboards and mice. There are even port replicators to use both devices on one port.

---

### Post by pablo180 on 2006-03-30
The reason that I bought the Belkin one was because it was meant to work, I did actually buy another adapter before that, but even though I got the drivers for it, it still wouldn't work (the drivers wouldn't install). 

So I then opted for the Belkin one as the drivers were included in Ubuntu and figured that I couldn't go wrong! 

I have loaded up the Pegasus module (just added it to the modules file) and it seems to load up fine. I don't have any problems getting onto the internet, just the speed is very slow. 

I am using it on an old laptop (IBM Thinkpad 600) and it just has one USB port, so there shouldn't be anything else using up the bandwidth. I am starting to think that it is just the speed that the laptop handles USB/Ethernet as I have tried the adapter on another PC both on Windows and Ubuntu 5.10 and both ran at full speed (but they are both USB2.0) so it just the laptop that has the problem. 

I did initially intend to go the PCMIA card route but read that a lot of people had problems with getting the cards to work on the IBM Thinkpad 600 so I figured that a USB Adapter would be cheaper and less hassle!

Thanks a lot for all your help but I think that I am just going to have to accept that the laptop will only work at that speed with that adapter, and maybe look at investing in a network card.

---

### Post by roachk71 on 2006-03-30
Thinkpads are troublesome for quite a few. Sorry I couldn't be of more help...

---

