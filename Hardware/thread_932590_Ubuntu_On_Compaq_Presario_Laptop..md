---
title: "Ubuntu On Compaq Presario Laptop."
date: 2008-09-28
forum: Hardware
---

### Post by xrecar on 2008-09-28
Hello everyone. I've been looking around and apparently everybody has my problem and not good solutions. I recently bought a Compaq Presario CQ50-115NR laptop, which so far I enjoy a lot and I consider it was worth the price. However, I'm not a vista fan, as a matter of fact I use ubuntu on my Desktop PC (where I am not at the moment)and I REALLY NEED to get ubuntu working on it, I need it for college.

So here is the thing:
Ubuntu Disc works fine and boots up perfectly but I have a few problems with the drivers:

1) Graphics card driver is not suitable for the laptop (this is what I have in my knoledge so far) 
******2) Trackpad button (the one to enable it/disable) brings up the ubuntu help page (I have no clue why)
******3) WiFi Button doesn't work (to enable/disable)
4) apparently there is no good driver for the WiFi.

****** = vefified by me

well, this si pretty much it, I really want ubuntu on my laptop any any help is great. If someone has my same problem, can you post up some info about it? or link to it?

Thanks sooooo much in advance.

---

### Post by sergiom99 on 2008-09-28
please post some of your laptop's specs, as well as the outputs of these commands typed in a console:
```
lspci
``````

lsusb
```

I've seen some postings about (2) [http://ubuntuforums.org/showthread.php?t=904143&highlight=touchpad+center](http://ubuntuforums.org/showthread.php?t=904143&highlight=touchpad+center)
[http://ubuntuforums.org/search.php?searchid=48734044](http://ubuntuforums.org/search.php?searchid=48734044)

---

### Post by xrecar on 2008-10-01
sure, I'll run the live cd in a moment and post it. thanks for the interest!!!

Ok.... **These are the specs:**
Processor :     2.0GHz AMD Turion X2 RM-70
Memory    :     3GB at 800MHz
Hard drive:     200GB, 5,400rpm
Graphics  :    Nvidia GeForce 8200M G
[B]
The output you requested:[/B]

**lspci**
```

ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0845 (rev a2)
07:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)

```

**lsusb**

```

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c526 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$ 

```

**PS: I'm using a logitech wireless mouse and posting from the live CD**

---

### Post by sergiom99 on 2008-10-01
maybe some of these threads could be of any help for the graphics.
[http://ubuntuforums.org/search.php?searchid=48883686](http://ubuntuforums.org/search.php?searchid=48883686)

This should be your wifi card:
> Network controller: Atheros Communications Inc. Unknown device 002a (rev 01) but no more details besides the maker.

Are you using Ubuntu 8.04? 8.10 is due for release anytime this month, why not try the LiveCd and see if you get more luck with hard detection?

---

### Post by xrecar on 2008-10-01
Yes, I am looking forward to 8.10, though there is something that has me slightly worried. I read that the alpha of 8.10 is messing up Wireless cards (particullary intel ones). 

By The Way, mine is an Atheros AR5009 802.11 a/g/n WiFi Adapter And a NVIDIA nForce 10/100/1000 Mbps Networking Controller.

Thank you so much for your support, I'll keep researching on the drivers I need. I still find it funny how the enable/disable trackpad button brings up the ubuntu help center...

Again, Much thanks.

---

### Post by sergiom99 on 2008-10-02
The only issue I had with mine was the broadcom wireless that has to go by ndiswrapper, which I just dont care as long as it works.
Good luck and well see what happens with the new release.

---

