---
title: "Is my next desktop 100% compatible?? Help me to check"
date: 2008-09-23
forum: Hardware
---

### Post by SyL on 2008-09-23
I'm about to built up an new config for replace my old 5 years old desktop.
Here is the config i'm thinking about. 

Does anyone, could point out any compatibility issue with Ubuntu?
I did not find any!


**Motherboard**: [FONT=Arial, Helvetica][SIZE=2][FONT=Arial][SIZE=2]ASUSTeK P5Q3 Deluxe/WiFi-AP @n (Intel P45 Express) - ATX -
**CPU**: [/SIZE][/FONT][/SIZE][/FONT][FONT=Arial, Helvetica][SIZE=2][FONT=Arial][SIZE=2]Intel Core 2 Quad Q9550 - Quad Core ! Socket 775 FSB1333 cache L2 12 Mo 0.045 micron
**RAM**: [/SIZE][/FONT][/SIZE][/FONT][FONT=Arial, Helvetica][SIZE=2][FONT=Arial][SIZE=2]Crucial Ballistix 2 Go (Kit 2x 1 Go) DDR3-SDRAM PC3-12800 8-8-8-24 - BL2KIT12864BA1608
**Disk**: [/SIZE][/FONT][/SIZE][/FONT][FONT=Arial, Helvetica][SIZE=2][FONT=Arial][SIZE=2]Samsung SpinPoint Série F - HD753LJ - 750 Go 3" 1/2 7200 RPM 32 Mo Serial ATA II
**Video Card**: [/SIZE][/FONT][/SIZE][/FONT][FONT=Arial, Helvetica][SIZE=2][FONT=Arial][SIZE=2]ASUSTeK EN8600GT SILENT/HTDP/512M - 512 Mo TV-OUT/Dual DVI - PCI Express (NVIDIA GeForce 8600 GT)



Many Thanks for any inputs!

[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by Neo_The_User on 2008-09-23
Intel is not linux friendly. I highly recommend an AMD processor (1900+ or higher) and as for the motherboard, I would go with an nVIDIA or AMD motherboard. Whatever you do, if your going to be using your computer for graphics at all, DO NOT GET an Intel GPU. I heard they are really bad in linux. The regular GPUs by nVIDIA and Ati are hard enough to get working with full 3d hardware acceleration and all that OpenGL support (just a heads up)

How much do you plan on spending because If I had an idea of what price you are looking for then I could make pretty good recommendations for your wallet and Ubuntu. ;)

---

### Post by damis648 on 2008-09-23
> **Neo_The_User said:**
> Intel is not linux friendly. I highly recommend an AMD processor (1900+ or higher)

I disagree. That setup you have there seems like it should work quite well... I'd buy it.

---

### Post by Neo_The_User on 2008-09-23
eh, I'd never ever use an Intel card for linux. Intel has been with Microsoft with several years. That's why even those Alienware computers only have 1 model with an AMD chipset and processor (Aurora.)

What I used (before my power extension cable burned up but that was because of my GPU everybody has problems with)

AMD 1800+ Processor
nVIDIA nForce 2 motherboard
AGP 8X Graphics Card (a re-worked ATi Radeon 9800 PRO)
Sound-on-chip AC97 sound card (works good with ALSA)
Brand new CD-ROM reader and writer with DVD reading and writing capabilities

As of yesterday am I using:

AMD 1050 (1.0 GHz, the first K7 processor made)
nVIDIA GeForce 5900XT AGP
ASUS Motherboard (no idea what kind but its pretty old)
A 6 - 8 year old CD-ROM reader

Yes an Intel WOULD WORK but all the linux guys I talk to and from my own experience, I would not use an Intel processor. I think a VIA C7 would run better than that.

---

### Post by SyL on 2008-09-23
Thanks for your comments!

Up to now i only had AMD config, and I've always be satisfy with it. But recently the gap between AMD and Intel has grown ... Furthermore, I'm not interesting to get a 64 bits, and AMD has chose this way. That's way i wanted to go for an Intel CPU.

For the motherboard, [FONT=Arial, Helvetica][SIZE=2][FONT=Arial][SIZE=2]Intel P45 Express chips have good performance and [/SIZE][/FONT][/SIZE][/FONT]reputation (it's based on the P35 with the support of the DDR3 additionally). Are you sure that a nVidia chip will be better for Linux?

Which kind of issue you may get using an Intel (motherboard and CPU) box?
Anyone has a feedback on that topic?



Regarding the usage, this computer will be use as a central base for the house, and will also be use by my wife. So mainly the usage will be multimedia, home cinema, internet, and sometime coding (eclipse, tomcat, mysql, ... nothing heavy), no game (no time), ...


[FONT=Arial, Helvetica][SIZE=2][FONT=Arial][SIZE=2]

[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by SyL on 2008-09-23
> **Neo_The_User said:**
> 

How much do you plan on spending because If I had an idea of what price you are looking for then I could make pretty good recommendations for your wallet and Ubuntu. 



about 1500€

---

### Post by Neo_The_User on 2008-09-23
The motherboard you can have whichever one you want. Just make sure the motherboard has the correct slots for the hardware you want to use.

For example:
If the CPU uses AM2+ then make sure the motherboard supports AM2+
If the GPU is PCI Express 2.0 16X, make sure the motherboard supports PCI Express 2.0 16X

I just prefer the AMD motherboards because of the features. Don't get crazy with Crossfire and Quad SLI GPU processing. Ubuntu doesn't have much support if not any support for multiple graphics cards. ;)

Don't get too crazy with Intel Quad core either. The generic kernels only use a max of 2 cores (custom kernel configs will allow more)

Any ATi Radeon X series or HD series would work fantastically

Any nVIDIA card that is a normal GeForce GPU (not a 200 series and not a quadro) would work fantastic as well

Intel Dual core processor above 2.0 GHz would work (way better using a custom kernel config)

AMD Athlon X2 processor would get the most out of Ubuntu right out of the box (6400+ would get way too hot but a 4000+ series would work lightning quick so would a 5000+ series)

I would not recommend anything with Crossfire, SLI, Quad core processing, an AMD Athlon X2 6400+ or an nVIDIA GeForce 280

---

### Post by SyL on 2008-09-24
> **Neo_The_User said:**
> 
Don't get too crazy with Intel Quad core either. The generic kernels only use a max of 2 cores (custom kernel configs will allow more)

Intel Dual core processor above 2.0 GHz would work (way better using a custom kernel config)

AMD Athlon X2 processor would get the most out of Ubuntu right out of the box (6400+ would get way too hot but a 4000+ series would work lightning quick so would a 5000+ series)


I had a look around, and could not find anything stating that Linux Kernel has a limitation of 2 cores, but at contrary that the Kernel 2.6 takes full advantage of modern multicore processors.
There is quite a few people around using Intel Quad Core, as well.

Would you please point some of your sources?


[http://ubuntuforums.org/showthread.php?t=813368&page=2](http://ubuntuforums.org/showthread.php?t=813368&page=2)
[http://ubuntuforums.org/showthread.php?t=652312&highlight=Intel+Core+Quad](http://ubuntuforums.org/showthread.php?t=652312&highlight=Intel+Core+Quad)
[http://www.ideastorm.com/article/show/73275/Ubuntu_PCs_with_Quad_Core_processors](http://www.ideastorm.com/article/show/73275/Ubuntu_PCs_with_Quad_Core_processors)




> **Neo_The_User said:**
> 

Any ATi Radeon X series or HD series would work fantastically

Any nVIDIA card that is a normal GeForce GPU (not a 200 series and not a quadro) would work fantastic as well

I would not recommend anything with Crossfire, SLI, Quad core processing, an AMD Athlon X2 6400+ or an nVIDIA GeForce 280



Good tips for the video card!
Not planning to use SLI or Crossfire.

Thanks for your input :-)

---

### Post by JDorfler on 2008-10-04
What about the ATI HD 3870?  I was wondering b/c looking at the description for it on Synaptic, it's not listed.  I'm in the same boat as the OP.  I'm looking to build a new PC.

---

### Post by Neo_The_User on 2008-10-06
ATI HD 3780 would be what I would buy if I had a PCIe motherboard.

P.S. If you get an ATi card, its really easy to replace the 3d accelerated drivers (System > Administration > Hardware drivers) It really makes it 3 times faster. When you get an ATI card, let me know and I will guide you through on making 3x faster without overclocking. Turning off desktop effects makes things faster as well including VLC video lan visualizations. ;) Not to sound cocky or anything but I am highly experianced with ATi drivers considering the fact I mess with them all day with my STABLE system.

---

### Post by SyL on 2008-11-05
up up up

---

