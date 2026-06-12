---
title: "Building a desktop and wondering if anyone has had any experience with any of these"
date: 2014-09-06
forum: Hardware
---

### Post by Nate_Olander on 2014-09-06
I've been researching and preparing to build a desktop for the first time. I've read various guides and looked at completed builds and, using PCPartPicker, I think I have the build I want. I'm now in the process of looking up reviews and wanted to make sure that these components are compatible with Ubuntu, or at least don't have any major issues. You can see the full build on PCPartPicker [here]("http://pcpartpicker.com/p/MDsZWZ").

First up, the CPU. It's an [AMD Athlon II X4 760K]("https://pcpartpicker.com/mr/newegg/amd-cpu-ad760kwohlbox") quad-core clocked at 3.8GHz. I don't plan on overclocking, at least not right away.

Second, the Motherboard. It's an [MSI A88X-G43 ATX FM2+ Motherboard]("https://pcpartpicker.com/mr/newegg/msi-motherboard-a88xg43").

Third, the RAM. I've chosen [Crucial Ballistix Sport 8GB (2x4GB) DDR3-1600]("https://pcpartpicker.com/mr/newegg/crucial-memory-bls2kit4g3d1609ds1s00").

The video card is an [EVGA GeForce GTX 750 1GB]("https://pcpartpicker.com/mr/newegg/evga-video-card-01gp42751kr"). I know it's a NVIDIA device, and I've heard that sometimes NVIDIA devices can be problematic after updates. This is one of the components I really would like to get input on.

For storage I'm getting a [WD Digital Caviar Blue 1TB 3.5" 7200RPM HDD]("https://pcpartpicker.com/mr/newegg/western-digital-internal-hard-drive-wd10ezex") and a [Sandisk Ultra Plus 128GB 2.5" SSD]("https://pcpartpicker.com/mr/newegg/sandisk-internal-hard-drive-sdssdhp128gg25").

For the OS I'll probably be using either Ubuntu 14.10 or Lubuntu 14.10 running Unity, with the OS, software, and home partition on the SSD and the rest on the HDD.

Thanks for any input!

---

### Post by Bucky Ball on 2014-09-06
Welcome. 

You might like to have a look at the last link in my signature regarding building a Linux machine. It is dated (and needs a little edit/update) but the principles remain. Won't help with your specific components, but you'll get some ideas. As you'll notice from the tutorial, one of my main points is *buy a decent, efficient power supply!* Don't skimp on this or settle for a silver box generic PSU which is capable of taking out the components in your new machine, and possibly worse. Go for a name brand, 80 or 85+ PSU. 

A few bucks more at the start can save a lot of heartache further down the track. You don't mention anything about a PSU. Good luck.

PS: 14.10? Fine, but it's not released yet and will have only nine months support. Fine, if you don't mind upgrading your OS every nine months. If you do mind, I'd go with an LTS release, 14.04 LTS (supported until April 2019).

PPS: Just looked at your build link and that PSU looks fine, although I'm not familiar with the brand. You will notice it is 80+ and therefore will make the electricity available for use with your machine rather than create heat with it (silver box generic PSUs are generally 70% efficient, or worse, and good in winter!). The rest looks fine, too. ;)

---

### Post by weatherman2 on 2014-09-06
What is the purpose of this machine you are building?  What is the typical use?

Do you have any constraints?  Performance?  Power?  Budget?

---

### Post by Nate_Olander on 2014-09-06
> 14.10? Fine, but it's not released yet and will have only nine months  support. Fine, if you don't mind upgrading your OS every nine months. If  you do mind, I'd go with an LTS release, 14.04 LTS (supported until  April 2019).

I know. I've been using Ubuntu since 11.10, so I have a general idea of how Ubuntu releases work. Thanks for pointing it out though!

> What is the purpose of this machine you are building?  What is the typical use?

It's going to be my main PC for at least the next 3/4 years and its typical use is going to vary. I don't do much gaming, but I do plenty of graphics editing and hope to do some 3D and emulating if possible. It'll be used for school purposes (presentations, documents, etc.) and research, and software programming (Python/C/Java) as well as for working with the Raspberry Pi and Arduinos.

> Do you have any constraints?  Performance?  Power?  Budget?

The main constraint for me is Budget. I can only spend ~$500/$600 on the build, and from what I've seen, these are the components to use for this price range.

Thanks for your response!

---

### Post by CantankRus on 2014-09-06
Agree with **Bucky Ball** and the main concern is a quality psu. Have had cheap ones fail in the past.
Have always used nvidia and never had major problems using either the open source nouveau or proprietary driver.
Similarly, have always used AMD cpus in both windows for gaming and in linux no issues.

Whenever I build a PC I never buy the latest parts as the higher cost versus any noticeable user experience is negligible.(unless your gaming)
```
@Trusty:~$ inxi -b
System:    Host: Trusty Kernel: 3.13.0-35-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 1400.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.38
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1250.3GB (19.3% used)
```

---

### Post by Nate_Olander on 2014-09-06
Nice build you have there! What's the RAM on it? I would agree with you on the cutting-edge stuff, and, since I'm not gaming, I'm fine! The CPU is the only one I know production date on, and that's mid-Q2 2013, so not cutting-edge, but not outdated. I need to research that some mre, just to be safe and make sure I'm somewhat future-proofed.

---

### Post by Bucky Ball on 2014-09-07
Graphics and network card (particularly wireless) are the only things you really need to worry about ...

Hardware related to the two and released yesterday doesn't always work as no open-source drivers for them ... yet! ;)

---

### Post by Yellow Pasque on 2014-09-07
For $20 more ($10 if you can get the rebate), you can step up the GPU a bit to a GTX 750Ti with 2GB of RAM [http://www.newegg.com/Product/Product.aspx?Item=N82E16814487024](http://www.newegg.com/Product/Product.aspx?Item=N82E16814487024)

EDIT: I's also like to point out that you can save about $15 on the RAM. This kit has the same specs, and has a lower price and promo code: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820231314](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231314)
I'm not a fan of the "jaws" style heatsink on RAM, but unless you have a case window or a big heatsink, it shouldn't matter.

---

### Post by Nate_Olander on 2014-09-07
> Hardware related to the two - What's the two? Also, I'm probably not going to be getting a WiFi card right away, it's not in the budget what w. the SSD. However, do you know of any WiFi cards/brands that work with Ubuntu so I'll know what to look for?

---

### Post by Nate_Olander on 2014-09-07
I considered the GTX 750Ti, but I decided that I didn't really need the extra power. I'm still thinking about it, but as of right now I'm not going to get the Ti version, as I'm not planning on doing any heavy gaming (Minecraft maybe).

As for the RAM, I can get the RAM that I have (Crucial Ballistix) for the same price as the G.Skill you linked to, from [MicroCenter]("http://www.microcenter.com/product/382101/Ballistix_Sport_8GB_DDR3-1600_%28PC3-12800%29_CL9_Dual_Channel_Desktop_Memory_Kit_%28Two_4GB_Memory_Modules%29"). I've been watching the G.Skills RAM, as I know it's good, but for now I'll stick with the Crucial, unless the G.Skills has better reviews (which I researching now.)

Thanks for your input though!

---

### Post by Bucky Ball on 2014-09-07
> **Nate_Olander said:**
> - What's the two? 

Graphics and wifi. If they were released yesterday, they may not work.

---

### Post by Nate_Olander on 2014-09-08
Ah. I see. So, basically anything that hasn't been released within, say, the last 6 months, should be good? Are there certain brands to steer clear of?

---

### Post by Bucky Ball on 2014-09-08
> **Nate_Olander said:**
> Ah. I see. So, basically anything that hasn't been released within, say, the last 6 months, should be good? 

Probably. ;)

> **Nate_Olander said:**
> Are there certain brands to steer clear of?

Regarding wireless, unsure what to steer clear of, but know what has worked for me in the past, mostly, and that is Realtek. Atheros also pretty good. The thing to look for is the wireless chip on the card and not so much the brand of the card itself. I have a couple of wireless dongles, both with Realtek chips, both different brands, both work. D-Link is another that I think has a Realtek chip in it. But, of course, not all models wireless card models by a particular brand will use the same wireless chip manufacturer. 

As for graphics, I've used NVidia and ATI cards without issue, so really depends on the card, and I'm not really qualified to comment on which is best.

---

### Post by daniell59 on 2014-09-11
Did you mention the case that you will be using? A good case really enhances the buidling experience.

---

### Post by oldrocker99 on 2014-09-11
> I know it's a NVIDIA device, and I've heard that sometimes NVIDIA devices can be problematic after updates. This is one of the components I really would like to get input on.

The only problem I have had with a nVidia card is that I didn't do this first:
```
sudo apt-get install dkms
``` 

Dkms makes sure that the driver you installed will get hooked to a new kernel, otherwise, you'll have to reinstall the driver every time there's a kernel update.

---

