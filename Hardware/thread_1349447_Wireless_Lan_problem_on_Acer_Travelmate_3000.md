---
title: "Wireless Lan problem on Acer Travelmate 3000"
date: 2009-12-08
forum: Hardware
---

### Post by tomshane on 2009-12-08
I installed Ubuntu 9.10 last night on my laptop. This is my first time with Ubuntu.  Everything seems great except that when I push the button on the laptop to enable the wireless connection it just flashes, it never turns on all the way. This is the same behavior I get in windows before the driver is installed.  I've looked around, but I can't see how to install a driver for it.  I'm sort of feeling around in the dark since I have no experience with Ubuntu, and little with Linux.  In another thread people asked for the output of lspci so here it is:
Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

I appreciate all help.

---

### Post by coffeecat on 2009-12-08
> **tomshane said:**
> Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

That chipset should work out of the box. The drivers for the Intel range of wireless devices are included in a default install so you don't need to install anything. In fact, when I briefly tried the Beta of Karmic on my old Sony laptop with that Intel wireless chipset, it worked just fine.

First thing. Have a look for the Network Manager icon on the top panel towards the right. See my screenshot - that's how it appears before it makes a connection. It's between the volume control and the message (looks like an envelope) icon. Click on it. Does it show wireless networks? If it shows your network and you click on that, can you connect?

If not, open a terminal and post the output of these two commands:

```
ifconfig
sudo lshw -C network
```You'll need to copy and paste - there's a lot of output. Please enclose the output in [noparse]```

```[/noparse] brackets.

---

### Post by tomshane on 2009-12-08
You have solved my problem.  I looked everywhere EXCEPT there.  My icon is two wires plugged together, I assume because I was using wired so I could post here, so I figured that wasn't the wireless connection manager.  Of course when I clicked on it the wireless option was there.  This is an oldish laptop I figured everything would work out of the box so I was surprised when it didn't.  Of course it was working, I just didn't know where to look.  I was looking around for a wireless type icon.  Sure enough once I had the wireless connected I pulled out the wired connection and the icon switched to a wireless icon.

---

### Post by coffeecat on 2009-12-08
> **tomshane said:**
> You have solved my problem.  I looked everywhere EXCEPT there.

Excellent. I'm glad it's solved.

---

