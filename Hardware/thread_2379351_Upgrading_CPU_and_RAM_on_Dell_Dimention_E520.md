---
title: "Upgrading CPU and RAM on Dell Dimention E520"
date: 2017-12-04
forum: Hardware
---

### Post by mitch.gray on 2017-12-04
Hey guys just wondering if i got the right ram for my desktop, i already have been told i can handle 2gb sticks of ram and that even though dell says i can only handle 4gb of ram, that i can get it up to 8gb, willing to give more info if im directed to do so, not great at ubuntu yet the RAM i bought is [Kingbox 8GB 4x 2GB DDR2 800Mhz PC2-6400 240Pin Low density SDRAM Memory]("http://www.ebay.ca/itm/For-Kingbox-8GB-4x-2GB-DDR2-800Mhz-PC2-6400-240Pin-Low-density-SDRAM-Memory/272855476818?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2060353.m2749.l2649") [https://www.ebay.ca/itm/For-Kingbox-8GB-4x-2GB-DDR2-800Mhz-PC2-6400-240Pin-Low-density-SDRAM-Memory/272855476818?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2060353.m2749.l2649](https://www.ebay.ca/itm/For-Kingbox-8GB-4x-2GB-DDR2-800Mhz-PC2-6400-240Pin-Low-density-SDRAM-Memory/272855476818?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2060353.m2749.l2649). and was wondering if anyone can tell me the best CPU my computer can handle? i just ordered a [Intel Core 2 Duo E8500 Dual-Core CPU 3.16 GHz 1333 MHz LGA 775/Socket T]("http://www.ebay.ca/itm/Intel-Core-2-Duo-E8500-Dual-Core-CPU-3-16-GHz-1333-MHz-LGA-775-Socket-T/252179112505?ssPageName=STRK%3AMEBIDX%3AIT&_trksid=p2057872.m2749.l2649") and think i may be able to handle something better

---

### Post by mitch.gray on 2017-12-04
also infromation on my motherboard is here: [https://microdream.co.uk/pc-components/dell-dimension-5200-e520-lga775-wg864-motherboard.html#.WiSGJemnFxg](https://microdream.co.uk/pc-components/dell-dimension-5200-e520-lga775-wg864-motherboard.html#.WiSGJemnFxg)

---

### Post by mitch.gray on 2017-12-04
also am curious to know if [h=1]intel core 2 Q6600 CPU Core2 QUAD core would be better than  the intel core duo e8500 dual core i mentioned above[/h]

---

### Post by Yellow Pasque on 2017-12-04
> i just ordered a Intel Core 2 Duo E8500 Dual-Core CPU 3.16 GHz 1333 MHz LGA 775/Socket T and think i may be able to handle something better

From this thread, the E8500 (a 45nm "Wolfdale" core) won't work. It seems you can only use 65nm based CPU's (Conroe and Kentsfield) with 1066 FSB.
[http://en.community.dell.com/support-forums/desktop/f/3514/t/19287896](http://en.community.dell.com/support-forums/desktop/f/3514/t/19287896)

[http://en.community.dell.com/support-forums/desktop/f/3514/p/19304203/19588409](http://en.community.dell.com/support-forums/desktop/f/3514/p/19304203/19588409)
TL;DR version: The Q6600 is reported to work, but make sure you have latest BIOS before taking out old CPU. If the q6600 works, I would think the q6700 would, but don't quote me on that.

As for the best dual core, it looks like the E6700 is the best that works with the board.

---

### Post by mitch.gray on 2017-12-05
So would a quad core be better of an upgrade than to the dual core?

---

### Post by Yellow Pasque on 2017-12-05
> So would a quad core be better of an upgrade than to the dual core?

[http://www.cpu-world.com/Compare/704/Intel_Core_2_Duo_E6600_vs_Intel_Core_2_Quad_Q6600.html](http://www.cpu-world.com/Compare/704/Intel_Core_2_Duo_E6600_vs_Intel_Core_2_Quad_Q6600.html)

---

### Post by mitch.gray on 2017-12-05
I am only seeing  these 2 different ones
Intel Core 2 Quad Q6700 2.66GHz Quad-Core (HH80562PH0678MK ...
[https://www.ebay.com](https://www.ebay.com) &#8250; Intel-Core-2-Qu...


Intel Core 2 Quad Q6700 2.66GHz Quad-Core (BX80562Q6700) - eBay
[https://www.ebay.com](https://www.ebay.com) &#8250; Intel-Core-2-Qu...

---

### Post by Yellow Pasque on 2017-12-05
They're the same CPU. One of them may come with the heatsink if it's still in the box.
> 
    HH80562PH0678MK is an OEM/tray microprocessor
    BX80562Q6700 is a boxed microprocessor with fan and heatsink


---

### Post by mitch.gray on 2017-12-06
also does the ram i bought (link at top) appear to be compatible? I tried to research the best i could to if it is compatible or not and I am pretty sure it is but would like comfirmation. thanks again for all your help

---

### Post by Yellow Pasque on 2017-12-06
Quick google shows multiple reports of using 8GB DDR2-800 on the mobo, so I don't see any red flags. When you're using a kit that isn't validated for the mobo, there's no guarantee though.

---

### Post by mitch.gray on 2017-12-06
okay awesome! thanks again for all your help :)

---

### Post by gordintoronto on 2017-12-07
Dell says the MB can only handle memory sticks up to 1 GB. If some people have found that 2 GB sticks works, you might be in luck.

As for quad versus dual-core, it depends on your workload. I find that very few programs make effective use of multiple cores, and I seldom run more than one heavy-compute program at a time. In short, I don't want a 12-core CPU that runs at 2 GHz, I want a dual-core CPU that runs at 12 GHz!

Good luck!

---

### Post by mitch.gray on 2017-12-08
Can Anyone guide me to finding out what GPU is compatible with my dell dimension e520?

---

### Post by mitch.gray on 2017-12-08
> **gordintoronto said:**
> Dell says the MB can only handle memory sticks up to 1 GB. If some people have found that 2 GB sticks works, you might be in luck.

As for quad versus dual-core, it depends on your workload. I find that very few programs make effective use of multiple cores, and I seldom run more than one heavy-compute program at a time. In short, I don't want a 12-core CPU that runs at 2 GHz, I want a dual-core CPU that runs at 12 GHz!

Good luck!
i do have one stick of 2gb ram in my computer at this moment and 2 512 mb sitcks also, only reading as 2.4gb of ram though so fingers crossed that can get a full working 8gb once my items arrive, also have the intel core 2 quad q6700 on the way also. just trying to figure out how to find compatible GPU decent for gaming

---

### Post by Yellow Pasque on 2017-12-09
If you still have the original PSU, that limits your choice. Also, it looks like one of those oddball motherboards with a proprietary layout (i.e. you can't use a dual slot GPU and there may be other limitations like the length of the card). A GT1030 is probably the best thing you can stick in there.

>  only reading as 2.4gb of ram
The IGP and other hardware use some of the address space. If you put in 8GB and make sure "Memory remapping" is enabled in BIOS, you should have at least 7GB usable, You'll ahve more if you do add a discrete GPU.

---

