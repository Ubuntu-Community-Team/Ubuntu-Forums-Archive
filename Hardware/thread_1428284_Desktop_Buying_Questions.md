---
title: "Desktop Buying Questions"
date: 2010-03-12
forum: Hardware
---

### Post by jonathansizz on 2010-03-12
Hi everyone,

I'm in the market for a new desktop system. This system: 

[http://www.costco.com/Browse/Product.aspx?Prodid=11504954](http://www.costco.com/Browse/Product.aspx?Prodid=11504954)

looks great and is within my budget, but I have a couple of concerns.

Firstly, the graphics. I'm worried about ATI graphics on Linux, so should I just look for an NVIDIA system, or would ATI be okay?

Second, the integrated graphics seems to be the weak-point of that system, so I'm thinking of getting a graphics card for it anyway. I suppose I would be limited to ATI cards, but how do I know which cards would be compatible (I don't do much 3D gaming, but it would be nice to be able to take advantage of my hardware, and I'll probably be wanting to set up a virtual Windows environment at some point which I'd obviously like to be as snappy as possible)? 

Thirdly, I also want to be able to use two monitors (probably both DVI). Would this be easy to set up in Linux? I guess that would also depend on the graphics card?

Help appreciated!

---

### Post by Brando753 on 2010-03-12
Im not sure what your looking for, This computer looks for the most part compatible with linux. Although ATI support isn't as great as NVIDA support. However it is still usable. As a computer Builder for Linux the thing that concerns me the most is its 300W Power supply this will limit future upgrades. Reply with what you mainly use your computer for, I will better be able to say if this is good for your application.

---

### Post by srs5694 on 2010-03-12
The on-board video does *not* limit your choices for add-on video cards. In theory, you should be able to use any add-on card with any brand of chipset you like, provided you've got a compatible slot. In practice, there are occasional weird incompatibilities, but I wouldn't worry about that at the moment.

Getting a multi-head display working can be either very easy or very hard, depending on the specific hardware and software involved. I recommend you research the specifics for any add-on card you plan to buy. If the card has two connectors, plan to use them both and research that card's dual-head features in Linux. If the card only supports one connector, you'll need to use it along with the motherboard's on-board video, which will make researching compatibility much harder. It's probably safer to go with a card with dual-head support in Linux from the single card.

In my experience, recent ATI cards work best with ATI's proprietary driver, but nVidia cards work with both the nVidia proprietary driver and the open source driver. (You give up a lot of 3D and other advanced features with the open source driver, but it works fine for most desktop uses, IMHO.) Personally, I detest both ATI's and nVidia's proprietary drivers, since they make upgrading kernels much more of a hassle; but most people want the 3D or other advanced features. Motherboards with on-board Intel graphics work fine with the open source Intel driver -- at least, most of them do. (I won't promise that every such system is fine.)

---

### Post by jonathansizz on 2010-03-12
Brando753: Thanks for replying. I am a scientist, so I will make use of the CPU and RAM for data analysis. In addition to the typical office, web and multimedia tasks (i.e. watching video and playing audio), I also do programming (the R statistical language, plus Ruby and Perl) and I'm planning on getting into web development soon. I also plan on SSHing into the system remotely, for file transfer and running command-line and graphical applications.

I'm planning on installing Linux and running Windows in a VM on the few occasions when I'll need it (mainly for MS Office when I'm collaborating with colleagues). I would assume the system I picked out would be powerful enough for this, but I would think a dedicated graphics card would help. I guess I could also consider getting Crossover instead of VMing, but as the system comes with Windows, it would probably be simple to make a Windows VM out of that.

I'll definitely want to set up dual monitors, so it's vital that this can be done comfortably. Again I assume that this means I'll need to buy a graphics card.

I don't think I'll need any kind of upgrades of hardware other than the graphics card. I normally like to buy a decent system and run it for 4-5 years, then get another one. If you know of another system with similar specs in the same price range that might be better for my needs, please let me know.

Thanks again.

---

### Post by jonathansizz on 2010-03-12
srs5694:

So any PCI-express card should work (I assumed I'd have to get one made for the AMD 760G chipset)? 

My approach should be to search for specific graphics cards that are known to work with dual-head in Linux?

Thanks for your help.

---

### Post by Brando753 on 2010-03-12
Again my concern here is an express x16 card will need to be hooked up with the power supply which may or may not be supported, this is a big gamble which could easily cost 150+ if your not sure. Also note that the windows pre-installed on this computer will not be able to be installed in a virtual machine. They are OEM installs which only work on the original hardware. If you need Microsoft Office install Wine then a program called Play on Linux which will set wine to work with it. What is your budget let me find a better model this might be a headache for what you want.

---

### Post by jonathansizz on 2010-03-12
That system is $700, and I was willing to pay up to $100 for a graphics card, so let's say under $800 total. I don't need a monitor, printer, etc: just the desktop unit itself. The quad core and 8GB DDR3 were very nice features, which I'd like to have in any system I end up buying (to give it staying power for 4-5 years without needing an upgrade). I don't really care about the size of the HD though; anything these days will be plenty (I don't need blu-ray either, just a DVD burner).

---

### Post by Brando753 on 2010-03-12
All right just give me a few minutes Ill respond as quickly as I can.

---

### Post by srs5694 on 2010-03-12
I'll add my support to the earlier comment about [WINE;](http://www.winehq.org) that should be more than adequate for running MS Office. It should be easier to set up than most VMs, it will be easier to launch Windows programs using Wine than in a VM, and the programs will integrate better with Windows (cut-and-paste will work, they'll use Linux printers, etc.). I'd only bother with a VM if I needed the whole OS for some reason or if the software didn't run under WINE.

Also, the [OpenOffice.org](http://www.openoffice.org) package, which is available for both Linux and Windows, does a very good job of reading and writing MS Office documents. I can't guarantee that it will work adequately for your needs, but it's worth trying. On rare occasion it's even better than MS Office. I've had it recover corrupted MS Word files that MS Word refused to open, for instance.

---

### Post by Brando753 on 2010-03-12
Thanks for waiting on me so long, I understand you need a fast processor 3.2+ and Fast Memory DDR3 but how important is the graphic card to you? are you doing heavy gaming or just number crunching. Do you need just a standard card that can handle two monitors or a high performance card?

Thanks,

Brandon Anderson

---

### Post by Brando753 on 2010-03-12
> **srs5694 said:**
> 
Also, the [OpenOffice.org](http://www.openoffice.org) package, which is available for both Linux and Windows, does a very good job of reading and writing MS Office documents. I can't guarantee that it will work adequately for your needs, but it's worth trying. On rare occasion it's even better than MS Office. I've had it recover corrupted MS Word files that MS Word refused to open, for instance.

Agreed, I find Open Office a much easier application then the new word. And I find it easier to open all sorts of fun File Types :P

---

### Post by jonathansizz on 2010-03-12
Brando753:

Mainly number crunching. My current system has a Sempron 64 3100+ and a Radeon 9250 (circa 2003!) which is almost adequate, so I'd imagine even integrated graphics or a standard graphics card on a modern system would be way better than that. Two monitors is the most important aspect (although I sometimes like to play TORCS, BZFlag, Flightgear etc. But none of the latest games or anything like that). 


srs5694:

I use OpenOffice myself; but for collaboration I sometimes need MS Office. Powerpoint seems to be the most troublesome program. I have tried installing Office 2003 under Wine on a couple of systems, but had no luck. I wouldn't mind shelling out the $30 for Crossover if necessary though.

---

### Post by Brando753 on 2010-03-12
again PlayonLinux in ubuntu software center is essentially a free crossover, you select microsoft office then insert the disk ans install :D

---

### Post by jonathansizz on 2010-03-12
I just tried playonlinux with Office 2003 on my current system with no luck. I think it's because I have one of those unlimited installer discs that universities sometimes give out!

I see on the Wine AppDB that Office 2000 gets a platinum rating, so I may try to pick up a copy of that: the older ones were better. Although then I'd be worried about not being able to open the new file format. So I should probably stick to OpenOffice anyway..

---

### Post by Brando753 on 2010-03-12
So what do you use it for specifically that open office cant do?

---

### Post by jonathansizz on 2010-03-12
In terms of features, OpenOffice is more than adequate. It's just compatibility that can be a problem. Most non-docx files are fine, but occasionally files get screwed up going back and forth between systems.

---

### Post by Brando753 on 2010-03-12
Here is a Makaniea Computer Customized for your needs,

[http://makaniea.com/product.php?id_product=31](http://makaniea.com/product.php?id_product=31)

Here is the Cheapest Dell I could find close enough to your specs.

[http://configure.us.dell.com/dellstore/config.aspx?oc=dxcwnn1&c=us&l=en&s=dhs&cs=19&kc=studio-xps-8100](http://configure.us.dell.com/dellstore/config.aspx?oc=dxcwnn1&c=us&l=en&s=dhs&cs=19&kc=studio-xps-8100)

Compare and ask any and all questions.

---

### Post by bedhead75 on 2010-03-13
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883229171](http://www.newegg.com/Product/Product.aspx?Item=N82E16883229171)

How about something like that for only $649.99?  Because it is designed as a "gaming" computer, it has a Nvidia GeForce 9800GT (I have one myself) which will give you easy dual-monitor Linux support just fine using the Nvidia drivers.  No worries about any ATI problems here. And since you say your Sempron 64 3100+ was "almost adequate", the Intel Core i3 (2.93GHz) chip in this will simply blow your old computer out of the water in terms of performance.  Some benchmarks show that the Phenom II X4 is a little faster than the Core i3, but it shouldn't make a huge difference for "real world" work.  The above rig only has 4gigs of ram, but you can easily add another 4gigs for less than $100 if needed.  I'm a scientist myself, and I don't think I've ever needed more than 4gigs of ram for computational work.

---

### Post by Brando753 on 2010-03-13
The above computer is a slower cpu with about .5 lower GHz which is a LOT but depending on what you do, it may be completely fine, The HD is half its size though. I must agree you wont need more then 4 GB memory the only thing to note is you will not be able to upgrade the memory on that computer easily. It only has two Memory slots so you can expect to pay a minimum of $315 to upgrade. On another note the memory is a slower standard 1333.

---

### Post by bedhead75 on 2010-03-13
I stand corrected about the Ram.  But the difference between Core i3 (2.93GHz) and Phenom II x4 (3.2GHz) is < 0.3GHz, and on stock cooling the Core i3 can be overclocked a lot more than the Phenom. For the relatively cheap price, and for the fact it comes with a Nvidia 9800GT and 500W power supply, makes it a pretty good deal.

---

### Post by Brando753 on 2010-03-13
Ah, I was referring to the phenom II X4 965 which is a 3.4GHz (the Makaniea link), Although that model displayed from new eggs pictures does not appear to have two outputs, double check that exact card, different manufactures offer cards differently.

---

### Post by jonathansizz on 2010-03-13
Okay, so I think I'm making progress.

1] Are you saying that 8GB is not going to be much better than 4GB at the moment, particularly if there are free slots available for later upgrade? But I take it that I am correct in thinking that DDR3 is the way to go for a new system?

2] So, the Makaniea compared to the Cyberpower has a much faster processor and spare RAM slots and faster RAM as well. I don't see many details on the linked page.

3] But how can I tell if the video card has two DVI slots, as some of that model do but some only have a single slot?


bedhead75: Note that I meant that what was 'almost adequate' about my old system was the 3D performance with the Radeon 9250; I definitely want the most powerful CPU within my budget, for overnight crunching sessions!

---

### Post by Brando753 on 2010-03-13
Memory _Speed_ is important Not so much the capacity. DDR3 is  the way to go for this build. 4GB will be PLENTY however You will want a faster cpu if possible. The Phenom II X4 965 is the fastest you can get for the money (This is in the Makaniea Model). For the Newegg model if you look at the pictures you will see the add-on card does not have two slots for DVI which is my concern. The Makaniea model does. Since the newegg one dose not state if it does I wouldn't know.

---

### Post by jonathansizz on 2010-03-13
> **Brando753 said:**
> For the Newegg model if you look at the pictures you will see the add-on card does not have two slots for DVI which is my concern. The Makaniea model does. Since the newegg one dose not state if it does I wouldn't know.


The Makaniea model does seem great, but how can you tell that it has two slots? I don't see any info about that at all.

Also, I've never heard of this company before. Are you familiar with their systems?

---

### Post by bedhead75 on 2010-03-13
Ahh, I misinterpreted what the OP originally said.  If you need CPU speed, benchmarks show that Intel Core 2 Quads with lower clock-speeds perform better than an AMD Phenom II X4's with higher clock speeds:

[http://www.phoronix.com/forums/showthread.php?t=15035](http://www.phoronix.com/forums/showthread.php?t=15035)

In terms of speed and cost-effectiveness, it's actually better to get a fairly cheap Core 2 Quad computer (< $600 even with [http://www.newegg.com/Product/Product.aspx?Item=N82E16883241021](http://www.newegg.com/Product/Product.aspx?Item=N82E16883241021)), over-clock it, and then spend around $70 on an energy efficient Nvidia GeForce GT 240 that DOES have multiple monitor support, requiring only a 300W power supply ( [http://www.amazon.com/exec/obidos/ASIN/B002VUCCVC/ref=nosim/7240466-rg2304-00-20](http://www.amazon.com/exec/obidos/ASIN/B002VUCCVC/ref=nosim/7240466-rg2304-00-20) and check [http://www.nvidia.com/object/product_geforce_gt_240_us.html](http://www.nvidia.com/object/product_geforce_gt_240_us.html) for minimum power specs. ).  A Core 2 Quad Q9300 overclocked even on stock cooling will perform around the same level, or even better than the Phenom II's.  

The speed of your RAM, and whether it's DDR3 or DDR2 actually makes an insignificant difference in terms of real world application, as long as you have enough RAM.  Look up RAM benchmarks to convince yourself that a one second difference in speed, in a process that takes several minutes to complete, can be called "insignificant".  Unless you're doing a lot of video editing, 4gigs of RAM should be enough.  

Since you said you don't care to upgrade because you'll be planning on replacing the computer after 4 or 5 years, this is the cheapest and possibly even faster (CPU performance-wise) solution.

---

### Post by Brando753 on 2010-03-13
Well I picked the model out because it uses a BFG GeForce 9800 GT 512MB, Which has dual DVI ports. Ive recommended this company since I bought a Desktop from them it is the older MX series.

---

### Post by Brando753 on 2010-03-13
> **bedhead75 said:**
> Ahh, I misinterpreted what the OP originally said.  If you need CPU speed, benchmarks show that Intel Core 2 Quads with lower clock-speeds perform better than an AMD Phenom II X4's with higher clock speeds:

[http://www.phoronix.com/forums/showthread.php?t=15035](http://www.phoronix.com/forums/showthread.php?t=15035)

In terms of speed and cost-effectiveness, it's actually better to get a fairly cheap Core 2 Quad computer (< $600 even with [http://www.newegg.com/Product/Product.aspx?Item=N82E16883241021](http://www.newegg.com/Product/Product.aspx?Item=N82E16883241021)), over-clock it, and then spend around $70 on an energy efficient Nvidia GeForce GT 240 that DOES have multiple monitor support, requiring only a 300W power supply ( [http://www.amazon.com/exec/obidos/ASIN/B002VUCCVC/ref=nosim/7240466-rg2304-00-20](http://www.amazon.com/exec/obidos/ASIN/B002VUCCVC/ref=nosim/7240466-rg2304-00-20) and check [http://www.nvidia.com](http://www.nvidia.com) for minimum power specs. ).  A Core 2 Quad Q9300 overclocked even on stock cooling will perform around the same level, or even better than the Phenom II's.  

The speed of your RAM, and whether it's DDR3 or DDR2 actually makes an insignificant difference in terms of real world application, as long as you have enough RAM.  Look up RAM benchmarks to convince yourself that a one second difference in speed, in a process that takes several minutes to complete, can be called "insignificant".  Unless you're doing a lot of video editing, 4gigs of RAM should be enough.  

Since you said you don't care to upgrade because you'll be planning on replacing the computer after 4 or 5 years, this is the cheapest and possibly even faster (CPU performance-wise) solution.

From my past experiences this is true when encoding Video, However when working with non-video dependent applications regardless of architectural differences of the cpu a higher frequency is more important. The Phenom II X4 series has out performed almost all processors I have seen in the past. Now I do agree with 4gb being plenty however DDR3 is QUITE significant difference from DDR2 and DDR. using a slower memory will cap the performance of you computer. Having used both DDR, DDR2, and DDR3 and can assure you the difference is noticeable.

---

### Post by bedhead75 on 2010-03-13
[http://www.extremetech.com/article2/0,2845,2328804,00.asp](http://www.extremetech.com/article2/0,2845,2328804,00.asp)

In the end, it all depends on whether paying that extra price premium for the latest and newest hardware is worth that extra 5% boost in real world performance.  We're not talking Semprons versus Core i7's here. Various benchmarks show that the real world differences between C2Q's versus Phenom II X4's, and DDR2 versus DDR3 RAM are on the order of a few percent.

---

### Post by Brando753 on 2010-03-13
Well with the CPU Benchmark the difference was .14GHz between CPU's the model you brought up is a difference of .9GHz That is HUGE, another factor to consider would be is the model you presented Overclockable? A lot of Motherboards do not support over clocking, Also If you want your computer to last 4-5 years over clocking will significantly lower the pcs lifetime. So I cant recommend that method. As for memory Standards Again I must recommend DDR3 not only do I consider it a notable difference but it is the incoming standard. If your looking to have a pc last a while you should keep up with the newer standards as they will be easier to replace parts for rather then older memory configs.

---

### Post by bedhead75 on 2010-03-13
...I just fail to see how last generation's C2Q's and DDR2 Ram would ever be inadequate for running Open Office, Linux, and overnight number crunching sessions within the next 4 or 5 years.  Too many people are needlessly buying $1000 e-mail and web-surfing machines.

---

### Post by cascade9 on 2010-03-13
> **jonathansizz said:**
> Brando753: Thanks for replying. I am a scientist, so I will make use of the CPU and RAM for data analysis. In addition to the typical office, web and multimedia tasks (i.e. watching video and playing audio), I also do programming (the R statistical language, plus Ruby and Perl) and I'm planning on getting into web development soon. I also plan on SSHing into the system remotely, for file transfer and running command-line and graphical applications.

I'm planning on installing Linux and running Windows in a VM on the few occasions when I'll need it (mainly for MS Office when I'm collaborating with colleagues). I would assume the system I picked out would be powerful enough for this, but I would think a dedicated graphics card would help. I guess I could also consider getting Crossover instead of VMing, but as the system comes with Windows, it would probably be simple to make a Windows VM out of that.

For data analysis, in your price range, I'd be looking for a X4 945/955/965. You arent going to need a 'gaming' video card, even a 8400 GS with dual DVI will give you all you want for multimedia. 

4GB will work, but if your planning on running VMs, 8GB is a better choice IMO.  

> **Brando753 said:**
> Here is a Makaniea Computer Customized for your needs,

[http://makaniea.com/product.php?id_product=31](http://makaniea.com/product.php?id_product=31)

Here is the Cheapest Dell I could find close enough to your specs.

[http://configure.us.dell.com/dellstore/config.aspx?oc=dxcwnn1&c=us&l=en&s=dhs&cs=19&kc=studio-xps-8100](http://configure.us.dell.com/dellstore/config.aspx?oc=dxcwnn1&c=us&l=en&s=dhs&cs=19&kc=studio-xps-8100)

Compare and ask any and all questions.

Aaprt from having may more video card than the OP needs (eats more power than a lower version, costs more, just a waste of money), the Makaniea looks pretty good. I wont if they would build one with 8GB/9400/9500 GT  with dual DVI?  

As for dell- yuck. I really dont like corporate computers. 

> **Brando753 said:**
> From my past experiences this is true when encoding Video, However when working with non-video dependent applications regardless of architectural differences of the cpu a higher frequency is more important. The Phenom II X4 series has out performed almost all processors I have seen in the past. Now I do agree with 4gb being plenty however DDR3 is QUITE significant difference from DDR2 and DDR. using a slower memory will cap the performance of you computer. Having used both DDR, DDR2, and DDR3 and can assure you the difference is noticeable.

Yers, it is. Comparing the phoronix link the following, the difference is quite shocking- 

[http://www.hardcoreware.net/amd-vs-intel-100-150-dollar-cpu/7/](http://www.hardcoreware.net/amd-vs-intel-100-150-dollar-cpu/7/)

Linked to the pages with the 'number-cruching' benchmarks, showing that a AMD 945/DDR3 is is quite a bit faster than a C2Q 8300/DDR2. A 965 would be faster still. (yes, I am aware that benchmaring will change from site to site).

> **Brando753 said:**
> Well with the CPU Benchmark the difference was .14GHz between CPU's the model you brought up is a difference of .9GHz That is HUGE, another factor to consider would be is the model you presented Overclockable? A lot of Motherboards do not support over clocking, Also If you want your computer to last 4-5 years over clocking will significantly lower the pcs lifetime. So I cant recommend that method. As for memory Standards Again I must recommend DDR3 not only do I consider it a notable difference but it is the incoming standard. If your looking to have a pc last a while you should keep up with the newer standards as they will be easier to replace parts for rather then older memory configs.

Well, overclocking wont always do that...but it can do, and IMO its only really a worth it for 'tweakers'- people who know what they are doing and can diagnose problems quickly and accurately. 

As for pure Ghz- ignore it, mostly. Architecture makes a big difference (as does L2 and L3 cache, mermeory interface speeds, etc). If it didnt, the fastest CPU around would still be a 3.8Ghz P4. 

Agreed on DDR3.  

> **bedhead75 said:**
> ...I just fail to see how last generation's C2Q's and DDR2 Ram would ever be inadequate for running Open Office, Linux, and overnight number crunching sessions within the next 4 or 5 years. Too many people are needlessly buying $1000 e-mail and web-surfing machines.

Agreed on '$1000 email and websurfing mahcines'. Its silly. Anything thats been posted in this thread will have no issue with open office and linux as well. As for number cruching- yeah, a C2Q will do it, but the AMD Phenom II X4s will do it faster, unless you want to factor in overclocking..and its not like you cant overclock AMDs as well. IMO its not really an option forthe OP so its not worth going into the relative merits of AMD vs Intel for overclocking. 

Does anyone know if newegg will actually build a PC for you? If the OP doesnt feel confident in assembling a PC (a lot of people arent) it would be a easy way to get exactly what is wanted, for the best pirce..without useless things like GT 9800 video cards.

---

### Post by Brando753 on 2010-03-13
Newegg from my latest knowledge will not, although I know Makaniea will customize any of their models if you send them an email. Thats how I built mine :)

---

### Post by bedhead75 on 2010-03-13
[http://www.ibuypower.com/Store/Configurators.aspx?mid=422](http://www.ibuypower.com/Store/Configurators.aspx?mid=422)


This company works too...whatever is cheaper for you.  Take that configuration for example, scale up the CPU and scale down the GPU to the minimum required for dual-monitor support (you can scale down the power supply accordingly too), and you can remain in your price range < $800.

---

### Post by jonathansizz on 2010-03-13
I want to thank everyone for their help. I think I know what I'm looking for now!

---

### Post by jonathansizz on 2010-03-14
Okay guys how about this, from Cyberpower:


# CD: LG 22X DVD±/±RW + CD-R/RW Dual Layer Drive (BLACK COLOR)
# CD2: 16X DVD ROM [+22] (BLACK COLOR)
# CAS: CoolerMaster Elite 310 Mid-Tower Case with See-Thru Side Panel [+7] (Blue Color)
# CS_FAN: Default case fans
# CPU: AMD Phenom™II X4 965 Black Edition Quad-Core CPU w/ HyperTransport Technology [+20]
# FAN: Asetek LCLC 120 Liquid Cooling System 120MM Radiator & Fan (Extreme Cooling Performance + Extreme Silent at 20dBA)
# FLASHMEDIA: INTERNAL 12in1 Flash Media Reader/Writer (BLACK COLOR)
# HDD: Single Hard Drive (500GB SATA-II 3.0Gb/s 16MB Cache 7200RPM HDD)
# MULTIVIEW: Non-SLI/Non-CrossFireX Mode Supports Multiple Monitors
# MOTHERBOARD: MSI 770-G45 AM3 770 Chipset CrossFireX Support DDR3 Socket AM3 ATX Mainboard w/ 7.1 HD Audio, GbLAN, USB2.0, SATA-II, RAID, 2 Gen2 PCIe, 1 PCIe X1, & 3 PCI
# MEMORY: 4GB (2GBx2) DDR3/1600MHz Dual Channel Memory Module (Corsair or Major Brand)
# NETWORK: Onboard Gigabit LAN Network
# NOISEREDUCE1: Power Supply Gasket [+5]
# NOISEREDUCE2: Anti-Vibration Fan Mounts [+9]
# OS: None - FORMAT HARD DRIVE ONLY
# POWERSUPPLY: 600 Watts Power Supplies (XtremeGear SLI/CrossFireX Ready Power Supply)
# RUSH: NO; READY TO SHIP IN 5~10 BUSINESS DAYS
# SERVICE: STANDARD WARRANTY: 3-YEAR LIMITED WARRANTY PLUS LIFE-TIME TECHNICAL SUPPORT
# SOUND: HIGH DEFINITION ON-BOARD 7.1 AUDIO
# USB: Built-in USB 2.0 Ports
# VIDEO: NVIDIA GeForce 9800 GT 1GB 16X PCI Express [-14] (Major Brand Powered by NVIDIA)

# _PRICE: (+766)

Phenom II X4 965, 4GB 1600MHz DDR3, even the GeForce 9800 video card (I could save another $45 by dropping down to the 9500, which I may do)
$766 with free UPS ground shipping! 

What do you think?

I just went with the default motherboard, how much difference would it make to upgrade it?

---

### Post by cascade9 on 2010-03-15
Not a bad setup, but I would change a few things myself- 

> **jonathansizz said:**
> 
# CD: LG 22X DVD±/±RW + CD-R/RW Dual Layer Drive (BLACK COLOR)
# CD2: 16X DVD ROM [+22] (BLACK COLOR) 

2x DVD drives is a waste, unless your planning on doing a lot of CD/DVD->CD/DVD copies. I'd also spend the extra $2 to get a Sony DVD-RW drive.

> **jonathansizz said:**
> 
# FAN: Asetek LCLC 120 Liquid Cooling System 120MM Radiator & Fan (Extreme Cooling Performance + Extreme Silent at 20dBA) 

Argh! dont get that watercooling system. I'd change to one of the air-coolers..less hassle, more reliable IMO (this from a long time watercooling user). Probably the Coolermaster V8....yeah, its $35 more, which shows you just how cheap the asus cooling unit is....But I'm not sure if I would get the V8, I would have to poke at some reviews to know just what CPU cooler I would get (if your interested I can do this). Only reason why I've said the V8 isbecause I've used one in the flesh (metal?) and it was a very good cooler. 

> **jonathansizz said:**
> 
# FLASHMEDIA: INTERNAL 12in1 Flash Media Reader/Writer (BLACK COLOR) 

No really need for this, unless you do a lot of card reading...I cant seem to remove it from the custom cyberpower sysems I've looked at though, you it might not be an option to do this. 

> **jonathansizz said:**
> 
# MOTHERBOARD: MSI 770-G45 AM3 770 Chipset CrossFireX Support DDR3 Socket AM3 ATX Mainboard w/ 7.1 HD Audio, GbLAN, USB2.0, SATA-II, RAID, 2 Gen2 PCIe, 1 PCIe X1, & 3 PCI 

Get a GigaByte GA-770T-USB3 AMD 770. Its not going to make more than 1-3% difference in performance, at best, but worth it if only for the USB3.0 support. IMO the gigabyte ultra durable series are better than the MSI motherboards as well. 

You could upgrade (to nVidia or ATI 790X/790FX chipset) but its really not worth it unelss you were planning on running video cards in SLI (nvidia chispets) or crossfire (790X/FX) unlocking a Phenom II X2/X3 to X4 (FX). Niether of which I think your going to do. 

> **jonathansizz said:**
> 
# VIDEO: NVIDIA GeForce 9800 GT 1GB 16X PCI Express [-14] (Major Brand Powered by NVIDIA)

# _PRICE: (+766)

Phenom II X4 965, 4GB 1600MHz DDR3, even the GeForce 9800 video card (I could save another $45 by dropping down to the 9500, which I may do)
$766 with free UPS ground shipping! 

Yes, if you not gaming I would. 9800s are fine gaming cards, but offer nothing for normal desktop use over the 9500.

---

### Post by jonathansizz on 2010-03-15
Thanks, points noted. I thought the media reader was worth the $3, as I'll probably use it occasionally.

One last question: what's the difference in performance between the 512MB and 1GB video card of the same model? The 1GB version is only $4 more than the 512MB; does it make any difference?

---

### Post by bedhead75 on 2010-03-15
If you have no intentions of over-clocking, you shouldn't ever get any CPU overheat issues even on stock air cooling. A cheaper air-cooler for your CPU is just fine.  

If you're sure you'll never do any serious gaming, go with the Nvidia 9500GT and save yourself some cash.  You also won't need a 600W power supply.  If you can downgrade that to a 500W or 450W power supply from a reputable company, you can save some cash and you'll still have sufficient power to keep your system stable.  The 1Gb versus 512mb of video memory factors in, I believe, when it comes to certain games with certain types of rendered textures.  If you do "light gaming", it won't matter.

I'd also recommend the Gigabyte MB with USB 3.0 over the MSI if you can afford paying the extra cost.

---

### Post by jonathansizz on 2010-03-15
I won't be overclocking, but what if I max out the processor for hours when I'm doing data analysis; wouldn't some extra cooling help with the longevity of the processor?

---

### Post by bedhead75 on 2010-03-15
I doubt that would be a problem if your case has adequate ventilation and you make sure vents don't get clogged with dust.  A better-than-stock air-cooler is more than adequate for your purposes. Many more people have problems with cheap power supplies blowing, and hard drives failing, than with CPU's "burning out" in a non-overclocked environment.  You also said you tend to change computers every 4 or 5 years, so CPU heat-related problems should be very slim for you even if you run overnight number crunching sessions.

---

### Post by bedhead75 on 2010-03-15
...btw, most non-overclocked CPU's on stock cooling only reach a max. temp. of 45C or so on load, even after hours.  Unlike high end video cards that reach 80C+ temps, it's really not that hot.

---

### Post by jonathansizz on 2010-03-16
Okay, I got the $9 CPU fan upgrade up from the standard, and another $9 upgrade from the default case fans. Total price: $750

Thanks for all your help everyone, I'll probably order it tomorrow!

---

### Post by cascade9 on 2010-03-16
> **jonathansizz said:**
> Thanks, points noted. I thought the media reader was worth the $3, as I'll probably use it occasionally.

One last question: what's the difference in performance between the 512MB and 1GB video card of the same model? The 1GB version is only $4 more than the 512MB; does it make any difference?

Not for normal desktop/multimedia use. It will with some games. 

> **bedhead75 said:**
> If you have no intentions of over-clocking, you shouldn't ever get any CPU overheat issues even on stock air cooling. A cheaper air-cooler for your CPU is just fine. 

If you're sure you'll never do any serious gaming, go with the Nvidia 9500GT and save yourself some cash. You also won't need a 600W power supply. If you can downgrade that to a 500W or 450W power supply from a reputable company, you can save some cash and you'll still have sufficient power to keep your system stable. The 1Gb versus 512mb of video memory factors in, I believe, when it comes to certain games with certain types of rendered textures. If you do "light gaming", it won't matter.

You shouldnt get overheating issues on stock cooling, but its a good idea IMO. I know a lot of people who run folding @ home, they tend to run at constant 85-100% load (sometimes for months at a time), and the differnce between a stock cooler and a good aftermarket cooler can add up faster than you might think. 

The good aftermarket coolers normally run bigger fans, which are quieter in general. 

I agree 100% on the power supply, but looking at the cyberpower website they seem to only offer much bigger power supply wattages than you will need in decent brands (600/650 watts + when a good 500 would be more than enough)  

> **jonathansizz said:**
> Okay, I got the $9 CPU fan upgrade up from the standard, and another $9 upgrade from the default case fans. Total price: $750

Thanks for all your help everyone, I'll probably order it tomorrow!

By the $9 upgrade, I take you mean the thermaltake maxorb? I'd give that one a miss...I admit, I am probably a bit biased, I've had more than my share of problems with the 'orbs'. Its a 'top down' blowing model...the 'blowing from the side' models give better airflow in the case, and come with bigger fans as well. 

Id be more liekly to go with the XtremeGear HP-1216X if you dont want to spend the extra $ to get the coolermaster V8. Even the Thermaltake V1 seems to be much better cooler. Direct comparison between the V1 and the Maxorb- 

[http://www.overclockersclub.com/reviews/ttmaxorb/3.htm](http://www.overclockersclub.com/reviews/ttmaxorb/3.htm)

Good luck with your order, no matter what parts you specifiy. ;)

---

