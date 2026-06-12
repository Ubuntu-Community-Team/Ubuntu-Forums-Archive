---
title: "graphic card recommendations appreciated (old hardware)"
date: 2021-07-09
forum: Hardware
---

### Post by ATSC on 2021-07-09
Hello :-)

I have a pretty old desktop computer that runs fine except for the onboard GPU that lags a bit too much. My knowledge about hardware is also as old as the computer.
I use the machine for basic personal routines (browsing, word processing, etc.) - resource-hungry applications are the exception.
Here are a few technical specs:
Mainboard: see here [https://www.fujitsu.com/de/products/computing/peripheral/mainboards/industrial-mainboards/d34462s.html](https://www.fujitsu.com/de/products/computing/peripheral/mainboards/industrial-mainboards/d34462s.html)
CPU: Intel Pentium dual core 2*2,8ghz (I was thinking about upgrading to a quad core sooner or later...)
- 8gb ddr2 ram

I'm on a budget - suggestions for a GPU that I can buy used are much appreciated! :-D

---

### Post by CatKiller on 2021-07-09
Wait.

The semiconductor supply shortage drove prices up to absurd levels, even for really old and poorly-performing kit. It was complete madness.

Wait for prices to come down again rather than buying anything right now.

---

### Post by Autodave on 2021-07-09
+1 with CatKiller: wait.  Save your money.  Prices will come back down again.

---

### Post by TheFu on 2021-07-09
Now that China has banned CryptoCurrencies, the huge crypto-farms are all dumping their nvidia 3060s for $30-50 less than retail prices. Of course, that is still 3x more than this Pentium PC is worth, so it won't help THIS person.

I have a dual core Pentium G3258. It is about to be gifted to an animal shelter to run their business after I replace it with a new-to-me Ryzen.  I'm all in on the AM4 platform for the next few years.  Upgrades are planned that just involve the CPU and nothing else.  I looked at doing that with my Intel-based systems and decided the price wasn't worth any performance gains. To get a sufficient performance boost, a new socket is required with Intel systems. Not so with Ryzen.  Same RAM. Same motherboard, just a new CPU can take a 6000 passmark system to over 20K passmarks.

---

### Post by linuux on 2021-07-10
> **ATSC said:**
> Hello :-)

I have a pretty old desktop computer that runs fine except for the onboard GPU that lags a bit too much. My knowledge about hardware is also as old as the computer.
I use the machine for basic personal routines (browsing, word processing, etc.) - resource-hungry applications are the exception.
Here are a few technical specs:
Mainboard: see here [https://www.fujitsu.com/de/products/computing/peripheral/mainboards/industrial-mainboards/d34462s.html](https://www.fujitsu.com/de/products/computing/peripheral/mainboards/industrial-mainboards/d34462s.html)
CPU: Intel Pentium dual core 2*2,8ghz (I was thinking about upgrading to a quad core sooner or later...)
- 8gb ddr2 ram

I'm on a budget - suggestions for a GPU that I can buy used are much appreciated! :-D
What's the local market like, there?   Just buy something used for now - if there's anything that's not too old.  Nvidia or AMD, doesn't matter.  I am looking for a GT 1030 or RX 550, 560, 570 etc.  GTX 1050 ti is pretty good but still a bit expensive.   Any of those cards will do and can be moved to a new computer if you are able to invest in a current generation computer in the near future.  

GT 1030 is the cheapest here, for me, and it's good for browsing, word processing - not so much for gaming.   

Yeah, it's better to wait but if the onboard GPU is causing lagging problems, that's frustrating.  It's possible, it's (also) cpu-related, too.  I had an older AMD system that was too slow - it couldn't play 1080p videos and forget about having more than a few tabs open.    Over 10 years old - it's not being used anymore. :)   Now, I'm running a Haswell computer and at least, it solved those problems....for the most part.

---

### Post by cryptearth on 2021-07-10
> **linuux said:**
> GT 1030 is the cheapest here, for me, and it's good for browsing, word processing - not so much for gaming.
I'm using a 1030 on my KVM host - and in fact it's quite capable for older games (many titles from the 2000's decade). If you have something newer (from the 2010's decade) that requires a bit more power - yea, the 1030 suffers/drowns - but if you ok to dial to 720p and lower the settings to below mid you can get at least some decent fps out of it - although than many stuff just looks pretty garbage.

---

### Post by TheFu on 2021-07-10
I have a 1030.  Didn't really want it, but I was forced into a new GPU to get support by the proprietary drivers and bought the cheapest of the current generation nVidia GPUs. My prior nVidia GPU was $40 and worked great for a decade. The prior GPU running nouveau drivers wouldn't go above 1080p resolution, though the hardware on a prior Ubuntu release had no issues with 1200p.  $70 fixed that issue for me. Not ideal, but a bargain to avoid frustration.

If I were doing it again, I'd avoid nVidia hardware.  AMD is better at basic GPU support being included in the kernel.  This assumes any built-in iGPU isn't sufficient.  On my Intel CPU systems, the onboard iGPU has been more than sufficient for my needs since 2012 when all the GPUs started including mpeg2 and h.264 decoding in hardware.

---

### Post by him610 on 2021-07-10
> ... pretty old desktop computer ... on a budget... 
We all have to live within our means. Upgrading your CPU may involve upgrading your motherboard too. 
How about providing some more details about your system? Please run this application from a terminal...
```
inxi -Fxz
```
Please display the results between the code tags.

---

### Post by linuux on 2021-07-10
> **TheFu said:**
> I have a 1030.  Didn't really want it, but I was forced into a new GPU to get support by the proprietary drivers and bought the cheapest of the current generation nVidia GPUs.  The prior GPU running nouveau drivers wouldn't go above 1080p resolution, though the hardware on a prior Ubuntu release had no issues with 1200p.  $70 fixed that issue for me. Not ideal, but a bargain to avoid frustration.

If I were doing it again, I'd avoid nVidia hardware.  AMD is better at basic GPU support being included in the kernel.  This assumes any built-in iGPU isn't sufficient.  On my Intel CPU systems, the onboard iGPU has been more than sufficient for my needs since 2012 when all the GPUs started including mpeg2 and h.264 decoding in hardware.I agree with you but I have a few comments and questions.

The OP didn't mention needing gaming.  I would like a 'gaming' card but I can't afford to get in that price range - also, I mostly wanted browsing, basic stuff (like OP, I presume).  So, I am stuck at looking at what is available.   With the current crypto craze and inflated gpu prices and many used card sellers overvaluing and asking for 'extra' for their card, the GT 1030 is one of those rare cards that haven't been overly expensive (although, probably still paying more). 

I agree, the AMD cards are probably a better choice/alternative for going with open source/FOSS drivers - at least, there are a lot of alleged advantages going with AMD/amdgpu driver.  But, the cheapest ones for the current generation are pretty expensive - plus, my added inconvenience is that I have a sff computer.   'Should have bought a tower should be my .sig, maybe?   I've seen a few cheap Rx 550 cards (2gb usually, some 4gb exist though) but they weren't low profile, single slot.  The other thing is that many are mining cards or were - which I don't have a problem with too much.  I was advised to get some settings outputs though - but, I dunno how many sellers will provide that kind of info.   There's still a lot of demand for graphics cards even though prices have gone down, a smidgeon, apparently.  

I am using Intel igpu and a 4K TV - I cannot get 4k resolution with it.  At least, when I try an iso/live media.   I also only get 4k resolution and 30 hz in Windows 10.   The hdmi to displayport adapter setup isn't ideal.   A graphics card will allow me hdmi to hdmi connection, 60 hz and 4k res (afaik).   Thus, I would like to get something, eventually, even if it has to be nvidia.   Hopefully, the nvidia 470 driver will allow for more compatibility with (using) XWayland.

---

### Post by linuux on 2021-07-10
> **cryptearth said:**
> I'm using a 1030 on my KVM host - and in fact it's quite capable for older games (many titles from the 2000's decade). If you have something newer (from the 2010's decade) that requires a bit more power - yea, the 1030 suffers/drowns - but if you ok to dial to 720p and lower the settings to below mid you can get at least some decent fps out of it - although than many stuff just looks pretty garbage.I've watched a bunch of videos showing gaming with a GT 1030 and they all support what you're saying.

---

### Post by cryptearth on 2021-07-11
> **ATSC said:**
> Mainboard: see here [https://www.fujitsu.com/de/products/computing/peripheral/mainboards/industrial-mainboards/d34462s.html](https://www.fujitsu.com/de/products/computing/peripheral/mainboards/industrial-mainboards/d34462s.html)
I've just noticed the localization "DE" - so I ausme you'Re from germany? If so, I have a nVidia GT 640 to send over for free. If you're interested feel free to send me a private message.

---

### Post by ATSC on 2021-07-18
Many thanks for all the helpful replies! :)

Please excuse my late reply I had to sort out a few real-life issues first.

> **him610 said:**
>  
Please run this application from a terminal...
```
inxi -Fxz
```

```
System:
  Host: benni-M2NS-NVM Kernel: 4.15.0-147-generic x86_64 bits: 64 
  compiler: gcc v: 7.5.0 Desktop: MATE 1.22.2 Distro: Linux Mint 19.3 Tricia 
  base: Ubuntu 18.04 bionic 
Machine:
  Type: Desktop Mobo: FUJITSU SIEMENS model: D2836-S1 v: S26361-D2836-S1 
  serial: <filter> BIOS: FUJITSU SIEMENS // Phoenix v: 6.00 R1.04.2836.S1 
  date: 07/21/2009 
CPU:
  Topology: Dual Core model: Pentium E6300 bits: 64 type: MCP arch: Penryn 
  rev: A L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 ssse3 vmx bogomips: 11199 
  Speed: 1701 MHz min/max: 1600/2800 MHz Core speeds (MHz): 1: 1600 2: 1600 
Graphics:
  Device-1: Intel 4 Series Integrated Graphics vendor: Fujitsu Solutions 
  driver: i915 v: kernel bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel Q45/Q43 (ELK) v: 2.1 Mesa 20.0.8 
  direct render: Yes 
Audio:
  Device-1: Intel 82801JD/DO HD Audio vendor: Fujitsu Solutions 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Sound Server: ALSA v: k5.4.0-58-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Fujitsu Solutions driver: r8169 v: kernel port: 2000 
  bus ID: 04:00.0 
  IF: enp4s0 state: down mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Fujitsu Solutions driver: r8169 v: kernel port: 3000 
  bus ID: 05:00.0 
  IF: enp5s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 931.51 GiB used: 232.52 GiB (25.0%) 
  ID-1: /dev/sda vendor: Toshiba model: HDWD110 size: 931.51 GiB  
  temp: 38 C 
Partition:
  ID-1: / size: 18.21 GiB used: 15.44 GiB (84.8%) fs: ext4 dev: /dev/sda1 
  ID-2: /home size: 889.27 GiB used: 217.07 GiB (24.4%) fs: ext4 
  dev: /dev/sda6 
  ID-3: swap-1 size: 9.31 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 35.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 168 Uptime: 1h 16m Memory: 7.57 GiB used: 1.70 GiB (22.5%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.5.0 Shell: bash v: 4.4.20 
  inxi: 3.0.32 


```


> **cryptearth said:**
> I've just noticed the localization "DE" - so I ausme you'Re from germany? If so, I have a nVidia GT 640 to send over for free. If you're interested feel free to send me a private message.

Yes, I'm from Germany, Thanks for your generous offer! :D I'll eventually get in touch with you!

---

### Post by TheFu on 2021-07-18
OUCH! [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+E6300+%40+2.80GHz&id=1103](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+E6300+%40+2.80GHz&id=1103)   Just 950 passmarks!  
My $200 chromebook from 2012 was 900 passmarks on the current scale. 
A desktop Core i5 from 2010 was 2900 passmarks. A $50 Pentium G3258 from 2014-ish, has 2000 passmarks.  I'd bet an 8th gen Core i5 would be a deal these days.  I have a laptop with one of those CPUs. It is efficient and fast.

A newer GPU will only help with watching video, I'm afraid. 

BTW, I did run 1 VM on my chromebook in 2012, but usually just used remote access into a VM server from the chromebook to access a much more powerful system.

As a desktop, if it uses standard ATX case, PSU, and all the other stuff, you could get a much faster, better, used, but newer MB+CPU for cheap and spend about 20 minutes swapping that into the case.  A $100 budget could do be an amazing upgrade.  Keep everything else. Just swap the MB+CPU for faster.  Call local small computer shops nearby and ask if they have any used MB+CPU combo deals for X Euros. I'd be surprised if the price for MB+Core I5 with 3000-5000 passmarks wasn't less than 100&#8364;.  I've seen entire off-lease laptops for that price.

---

### Post by mastablasta on 2021-07-21
> **ATSC said:**
> 
Yes, I'm from Germany, Thanks for your generous offer! :D I'll eventually get in touch with you!


the GT640 will extend the life for quite a few more years. i recently upgraded form Single core AMD (that has passmark about 450) and 4GB ddr2 ram. i could still play many old games with GT730 (which was actually 530 in disguise), so with 640 (which has newer chip than mine) you should be fine even if you want to play some newer titles on low setting.

the old PC is now waiting to be reused. i was thinking as video playing machine or some kind of server. 

i upgraded because i has some issues with youtube videos and some websites were slow to open as i have script blocker installed. so i reused components and due to current prices for GPU i just upgraded the motherboard, ram and CPU.  

for your use i agree - get an older PC if you can get it cheap or get a new motherboard, ram and CPU (which comes with GPU chip). older models of CPU are still available at some places and they are not really that much slower. i also bought an older model CPU.

yeah GPU prices are crazy. GTX 1650 should be 150 EUR, and they are selling them for 300. the old GT 1050 should be about 110-130 EUR and they are selling it for 220 EUR here. the gt 1030 should be about 60-70 EUR, they are selling the low profile version for 100-110 EUR and normal version for 130 EUR. AMD cards? they don't sell any here but the RX version which cost way too much (over 1000 EUR).

---

### Post by TheFu on 2021-07-21
nvidia will stop making their proprietary driver for the GT6xx line sooner than people realize.  My GT 7200 lost nvidia support at 16.04.
I don't think I'll be buying nVidia GPUs anymore, unless forced.  I've been buying their stuff 20 yrs now.  

I've had issues with AMD video support too from time to time. Had a APU lose support completely around 2015 when it was in an ITX case, so putting in a replacement wasn't an option. The E-350 was very slow already and the entire system was replaced by an Intel G3258 in a larger case. The Pentium G3258 is still going with 2 VMs running now. It is the main NAS for my network with over 32TB of storage. It doesn't really get used to play videos, but it can and does a fine job.  During the Olympics, it will be heavily used to record videos overnight.

I've been fortunate with the iGPU support from Intel. A few times, the Intel iGPUs have had terrible issues under Linux, but those were always for a different CPU than what I had. I dream of the day when AMD Ryzen CPUs have excellent iGPU support for zero premium.  Today, Ryzens with iGPUs are commanding $100 premiums.

---

### Post by mastablasta on 2021-07-22
> **TheFu said:**
> nvidia will stop making their proprietary driver for the GT6xx line sooner than people realize.  My GT 2700 lost nvidia support at 16.04.
I don't think I'll be buying nVidia GPUs anymore, unless forced.  I've been buying their stuff 20 yrs now.  

if i remember correctly they are supported until 2023, so with LTS kernel and all that should give you until 2027.

nvidia has / had better energy usage. maybe if AMD can come up with power saving GPU that performs ok i will look at it. at the moment AMD shelves are empty over here anyway (unless you go high end super premium).

[QUOTE]
 Today, Ryzens with iGPUs are commanding $100 premiums.

yes, they are, because they outsourced production and same chip manufacturer has to supply to multiple chip designers/brands. and they can raise prices just to get them produced ahead of queue.

intel has it's own production in US so no battles over chips and shorter supply chain. 

i still went with older model Ryzen as here it didn't have much difference in price (20 EUR) to similar intel. now i am wondering if maybe i made a mistake and should have gone with newer one (4xxx) and APU. it would currently be enough for my needs.  but what is done is done. this one will have to do until i can get a better GPU (which will force me to get a new monitor as well as i currently have 19" SVGA 4:3).

---

### Post by cryptearth on 2021-07-23
Well - what a coincidence I have a quite similar hardware setup around as you have - and just tested the 640 I'm about to send over as discussed privately.
I just quickly used Half-Life 2 as a short benchmark - depend on the settings I got as low as just 18 fps when every setting is cranked to max - but managed to get about 35 when dialing it back to about medium. So the card is quite able to handle at least this type of games.
I used the 390 driver as the ubuntu wiki said it's the driver to use for such an old card - and haven't bothered to try any newer or even windows (the system is REALLY slow - it took about 1 1/2 hours to get from bare metal into HL2 - mostly because the system only has two cores and only 100mbit NIC.
```
[COLOR=#000000]System:    Kernel: 5.11.0-25-generic x86_64 bits: 64 compiler: gcc v: 10.2.1 Desktop: GNOME 3.38.4 [/COLOR]           Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:   Type: Desktop System: ECS product: G31T-M7 v: 1.0 serial: <filter> 
           Mobo: ECS model: G31T-M7 v: 1.0 serial: <filter> BIOS: American Megatrends v: 080014 date: 02/25/2010 
Battery:   Device-1: hidpp_battery_0 model: Logitech M720 Triathlon Multi-Device Mouse charge: 55% (should be ignored) 
           status: Discharging 
CPU:       Info: Dual Core model: Intel Core2 Duo E7300 bits: 64 type: MCP arch: Penryn rev: 6 L2 cache: 3 MiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 ssse3 bogomips: 10640 
           Speed: 1990 MHz min/max: 1603/2670 MHz Core speeds (MHz): 1: 1990 2: 1749 
Graphics:  Device-1: NVIDIA GK107 [GeForce GT 640] vendor: eVga.com. driver: nvidia v: 390.144 bus ID: 01:00.0 
           Display: x11 server: X.Org 1.20.11 driver: loaded: nvidia unloaded: fbdev,modesetting,nouveau,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: GeForce GT 640/PCIe/SSE2 v: 4.6.0 NVIDIA 390.144 direct render: Yes 
Audio:     Device-1: NVIDIA GK107 HDMI Audio vendor: eVga.com. driver: snd_hda_intel v: kernel bus ID: 01:00.1 
           Sound Server: ALSA v: k5.11.0-25-generic 
Network:   Device-1: Qualcomm Atheros Attansic L2 Fast Ethernet vendor: Elite Systems driver: atl2 v: kernel port: ec00 
           bus ID: 02:00.0 
           IF: ens32 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 2.73 TiB used: 14.1 GiB (0.5%) 
           ID-1: /dev/sda vendor: Seagate model: ST3000DM008-2DM166 size: 2.73 TiB 
Partition: ID-1: / size: 1006.93 GiB used: 14.1 GiB (1.4%) fs: ext4 dev: /dev/sda2 
Swap:      ID-1: swap-1 type: file size: 3.83 GiB used: 85.3 MiB (2.2%) file: /swap.img 
Sensors:   System Temperatures: cpu: 53.0 C mobo: N/A gpu: nvidia temp: 57 C 
           Fan Speeds (RPM): N/A gpu: nvidia fan: 45% 
Info:      Processes: 192 Uptime: 1h 03m Memory: 3.83 GiB used: 1.56 GiB (40.6%) Init: systemd runlevel: 5 Compilers:  [COLOR=#000000]           gcc: 10.3.0 Packages: 1763 Shell: Bash v: 5.1.4 inxi: 3.3.01 v[/COLOR]
```

---

### Post by linuux on 2021-07-23
'Cheapest graphics cards are probably GT 1030 and RX 550 (nvidia and amd side).   I believe you can probably find these cards via European sites (to order from Germany)?   They appear to be quite common on newegg and amazon (probably sites in Europe too).   I am looking for the lower profile versions but I see the normal dual slot versions too - quite a lot of them.

GT 1030 doesn't support NVENC but pretty much everything else.  But, if someone is open to the 640, those cards are probably worth looking for.   They are newer although a bit more expensive.   You might be able to find some used - they are not good enough to be used as mining cards.  Both should be supported for a while.

---

### Post by TheFu on 2021-07-23
There are 2 1030 versions.  One with DDR5 DRAM and the other with slower, DDR4 DRAM.  Be careful which you buy. There's a big performance difference.  I have a fanless model with DDR5.  Again, I'd get an AMD GPU if Linux support were important.  There's a famous photo showing what Linus thinks about nvidia that is easily found.  nvidia support is much better on Ubuntu these days, if you run an LTS and use the **ubuntu-drivers autoinstall** command.  I know LTS support was a goal, but cannot say anything about non-LTS Ubuntu releases and nvidia.

---

### Post by cryptearth on 2021-07-24
> **linuux said:**
> 'Cheapest graphics cards are probably GT 1030 and RX 550 (nvidia and amd side).   I believe you can probably find these cards via European sites (to order from Germany)?   They appear to be quite common on newegg and amazon (probably sites in Europe too).   I am looking for the lower profile versions but I see the normal dual slot versions too - quite a lot of them.
Just for teh lolz I did a short search: Using a site for comparing market prices I found the cheapets 1030 for about 95€ while the cheapest 550 stated at around 120€.
I also tried to search on ebay - but as I don't like that platform for several reasons I not invested any more time after still in the 10€-15€ range full of old pci/agp cards, lots and lots of fans, brackets, anti-sagg-stands and other crap. Yes, I came accross ongoing auctions, one for a gtx670 (currently at around 12€, 3 days left) and a 1060 (about the same, but 6 days or so left) - and I'm sure someone with experience on the site is able to find the few good deals to save quite a lot ... but hey: I'm sending over my 640 for free - I don't need it anyway and it seems a perfect fit - even if it's just to get the card a couple more months before it finally ends up as e-waste anyway.
> **linuux said:**
> GT 1030 doesn't support NVENC but pretty much everything else. But, if someone is open to the 640, those cards are probably worth looking for. They are newer although a bit more expensive. You might be able to find some used - they are not good enough to be used as mining cards. Both should be supported for a while.
Oh yea, I had to learn THAT the hard way: Although off-topic, I explain why anyway: As I started to stream quite some time ago now I figured why not built a cheap 2nd system to offload the streaming to it. I already had a FM2 APU in mind - and designed the system around such. Little did I know back than that the elgato hd60 I chose (was the best option back then) is a bit of false advertising. Yes, it does have a h.264 asic on the card - BUT: it's only ever used with direct input-to-stream when using elgatos own software. And even if using that style it's only a 1-to-1 direct copy of the incoming hdmi stream (1080p / stereo audio) packed into rtmp with at most 8mbit/s - 10mbit/s of quality. No overlays, no alerts, no nothing - just directly streaming the hdmi input directly to the streaming service. If one want's anything more fancy or use any other streaming software than the elgato one the card only behaves as a very expensive paperweight offering an hdmi input - pointing a cheap webcam at your screen would get you far cheaper. One requires quite some hardware to use it - both a rather powerful cpu as well as a good gpu as encoder-accelerator.
I though any cheap modern gpu would do and so I ordered a 1030 - only to find out: it doesn'T offer any encoding acceleration (it ended up as the "system" gpu in kvm host). So I ended up ordering a 1650 - just as encoding accelerator for my stream system.
Fun fact: as my r9 290x died from overheating as I didn't noticed a failed fan in time at least I can use it to game and default back to the direct-stream with elgatos software ... I don't have a facecam anyway.

---

### Post by linuux on 2021-07-24
> **TheFu said:**
> There are 2 1030 versions.  One with DDR5 DRAM and the other with slower, DDR4 DRAM.  Be careful which you buy. There's a big performance difference.  I have a fanless model with DDR5.  Again, I'd get an AMD GPU if Linux support were important.  There's a famous photo showing what Linus thinks about nvidia that is easily found.  nvidia support is much better on Ubuntu these days, if you run an LTS and use the **ubuntu-drivers autoinstall** command.  I know LTS support was a goal, but cannot say anything about non-LTS Ubuntu releases and nvidia.Are you having any trouble using your card on Ubuntu?  I thought Ubuntu was criticized a little while ago for providing proprietary drivers (already) installed - because the Linux community supports FOSS so having them 'pre-installed' went against the ethics/philosophy etc.   Maybe I didn't explain that accurately but you probably know what I'm talking about.

In Ubuntu, AFAIK, you only have to 'click' the proprietary driver in Additional Drivers to 'enable' its use.  I'm not sure why people have so much trouble with it when installing.  I realize that there are potential problems whenever you upgrade your Linux version i.e. upgrading the kernel.   That's because the kernel modules/headers need to match up with the Nvidia modules/info (I don't know the exact terms/terminology but it's mostly a problem with version upgrades).   When there's a mismatch, the drivers don't work with X(org) or whatever which results in a black screen.   I have seen this when I used to install nvidia drivers 'the hard way' or manually.   

I think, as long as you understand the dynamics and concepts of what is happening and what is going wrong (and have an online connection with another computer or phone - so you can use internet to look up 'fixes' and recovery methods), you can deal with the nvidia proprietary driver.

In saying all that, though, the AMD(GPU) driver sounds a lot simpler and since it's ingrained properly in the kernel, much easier to deal with.   However, I think it also has a problem with kernel upgrades - if AMD doesn't have an updated driver ready or if there are changes, there's potential for it to cause problems too.   I read that bleeding edge distros have a lot of changes and thus, it is possible that using the free AMD driver can lead to some of these 'out-of-sync' issues or there is a delay in AMD driver updates.  

It's a pick your poison situation but the main reason for me to look at GT 1030 (DDR5) instead of the RX 550 - is because I am finding more used (cheaper) nvidia cards else I would pick an RX 550 (I still might but they are at least $60 more here).

---

### Post by linuux on 2021-07-24
> **cryptearth said:**
> Just for teh lolz I did a short search: Using a site for comparing market prices I found the cheapets 1030 for about 95&#8364; while the cheapest 550 stated at around 120&#8364;.
I also tried to search on ebay - but as I don't like that platform for several reasons I not invested any more time after still in the 10&#8364;-15&#8364; range full of old pci/agp cards, lots and lots of fans, brackets, anti-sagg-stands and other crap. Yes, I came accross ongoing auctions, one for a gtx670 (currently at around 12&#8364;, 3 days left) and a 1060 (about the same, but 6 days or so left) - and I'm sure someone with experience on the site is able to find the few good deals to save quite a lot ... but hey: I'm sending over my 640 for free - I don't need it anyway and it seems a perfect fit - even if it's just to get the card a couple more months before it finally ends up as e-waste anyway.

Oh yea, I had to learn THAT the hard way: Although off-topic, I explain why anyway: As I started to stream quite some time ago now I figured why not built a cheap 2nd system to offload the streaming to it. I already had a FM2 APU in mind - and designed the system around such. Little did I know back than that the elgato hd60 I chose (was the best option back then) is a bit of false advertising. Yes, it does have a h.264 asic on the card - BUT: it's only ever used with direct input-to-stream when using elgatos own software. And even if using that style it's only a 1-to-1 direct copy of the incoming hdmi stream (1080p / stereo audio) packed into rtmp with at most 8mbit/s - 10mbit/s of quality. No overlays, no alerts, no nothing - just directly streaming the hdmi input directly to the streaming service. If one want's anything more fancy or use any other streaming software than the elgato one the card only behaves as a very expensive paperweight offering an hdmi input - pointing a cheap webcam at your screen would get you far cheaper. One requires quite some hardware to use it - both a rather powerful cpu as well as a good gpu as encoder-accelerator.
I though any cheap modern gpu would do and so I ordered a 1030 - only to find out: it doesn'T offer any encoding acceleration (it ended up as the "system" gpu in kvm host). So I ended up ordering a 1650 - just as encoding accelerator for my stream system.
Fun fact: as my r9 290x died from overheating as I didn't noticed a failed fan in time at least I can use it to game and default back to the direct-stream with elgatos software ... I don't have a facecam anyway.Yeah, that's the only negative for the 1030 as far as I can tell - the feature set doesn't include NVENC.   The next card up that does is the 1050 ti.  I would look for one of those but they are expensive and I can only find them used - $100 more than the 1030.   But, it's more powerful than the RX 550 and I need a lp card anyway since I foolishly bought a sff computer.  I was desperate though and someone was selling a sff for $100.  

The other reason I need a discrete gpu is that the Intel igpu doesn't support 4k resolution - the sff only has display port so I need to use an adapter.  Thus, Linux OS only supports 1080p res on my 4K tv and in Windows, I am stuck at 30 hz.  A discrete gpu will solve all these issues.  They aren't major but kinda annoying.   I should have bought a tower but that would have been $80+ more.  

I don't know what advantages you get with NVENC over AMD encoding but many people tend to choose the nvidia card, right?   The RX 550 supports video encoding so it has more features over the GT 1030.  There's only one LP choice for that card though.   I can find normal, dual slot RX 550s (used and new) for various prices including as cheap as the used GT 1030s but they won't fit because they are normal height (although some are single slot and short in length).   Note to everyone:  don't choose sff computers unless you have measured it and know that the cards you want will fit!

---

### Post by TheFu on 2021-07-24
Whenever I've played with GPU encoding, the results haven't been great and always seemed fuzzy.  I don't live-stream, so a no-brand $65 HDMI 1080p capture device off amz running handbrake on a Ryzen creates very nice, small, videos. For example:
5890333202 (5.5G) for the original "real-time" capture and
1173110950 (1.1G) for the handbrake encoded version.  Both are h.264/AAC encoded, though I add a vorbis audio track to the 2nd version.  The audio encoding is just stereo since the source stopped using DD 5.1 audio for DD+, which isn't supported by any of the cheapo options. To get **any** audio, I have to use stereo audio settings from the source.  I have a few players that **do not** support h.265, so I don't use that vcodec.

I've not had issues with Intel iGPUs on 4K displays. Perhaps the wrong type of physical connection is being used?  DisplayPort and VGA appear to work fine.  
[https://ark.intel.com/content/www/us/en/ark.html](https://ark.intel.com/content/www/us/en/ark.html) is the Intel Specs search page. My Intel G3258 from 2014 supports  2560x1600@60Hz over display port and 1920x1200@60Hz over VGA, but only 1080p over HDMI.  The connection type matters.

My Core i5-8250 does 4096x2304@60Hz over displayport, but only 4096x2304@24Hz over hdmi.

Perhaps we are saying the same thing?

For playback, I have raspberry pi media players.  I don't have a full computer next to the projector. We strive to keep the noise down and computers or Xbox systems are just too noisy. A raspberry pi is silent.

Glad I've had the 1030 GT 2.5 yrs now as it was still 2x the cost of what I really wanted for a GPU at $70. Mine is in a KVM host. I got a 10xx-series to extend the support period 1 more generation, in theory.

BTW, not everyone uses the GUI for package management.  I don't have an "additional drivers" option on my systems, but the **ubuntu-drivers autoinstall** accomplishes the same thing and is much easier to post in these forums as an answer. That command produces output to help folks struggling if anything bad happens, unlike using a GUI.

---

### Post by cryptearth on 2021-07-24
> **TheFu said:**
> BTW, not everyone uses the GUI for package management.  I don't have an "additional drivers" option on my systems, but the **ubuntu-drivers autoinstall** accomplishes the same thing and is much easier to post in these forums as an answer. That command produces output to help folks struggling if anything bad happens, unlike using a GUI.
According to the ubuntu wiki there'Re several different versions of the nvidia driver all supporting different ranges of models. Does the auto-install also take this into account and only installs the highest useable driver that still supports the installed gpu?
For some reason I experienced a strange driver issue where the 1030 required a lower version but my 1650 required a higher one. For some odd reason both are incompatible with oneanother: The driver supporting the 1030 doesn't support the 1650 and vise-versa.
Unfortunately I'm not that fluent in linux to have install both drivers just with different names and then set the specific version for each device - but this shows that a multi-gpu system is not just limited by the back then "it has to be the very same card for them work together" but also of specific driver versions. Even one generation difference can break a system.

---

### Post by TheFu on 2021-07-24
I know that **sudo ubuntu-drivers autoinstall** works on my KVM host with a 1030 GT.  Due to some other oddities, I run that as part of my weekly patch script.  I don't allow automatic patching - or any patch nagging.  On 18.04, nvidia-driver-460 is the correct driver for that card.

On another KVM host, nvidia-driver-390 is the correct driver package for NVIDIA GF108 [GeForce GT 430], but I haven't actually looked at the screen on that system in a few months. All management and use is through ssh.  It is connected to a kvm-switch, so looking isn't THAT hard, but it doesn't run a GUI by default.

That would seem to say that sudo ubuntu-drivers autoinstall does the right thing some of the time, perhaps most of the time, but I really don't know.  Whatever people do, don't go grab the driver from nvidia's website.  Always, always, stick with drivers provided through Canonical's package management.  It is safe to get information about the correct driver version from the nvidia website, just don't download drivers from there.

---

### Post by cryptearth on 2021-07-24
Thanks for that advice. Will stick to it even I'm used to goin to vendors sites and download drivers from there on windows.

---

### Post by linuux on 2021-07-24
> **TheFu said:**
> Whenever I've played with GPU encoding, the results haven't been great and always seemed fuzzy.  I don't live-stream, so a no-brand $65 HDMI 1080p capture device off amz running handbrake on a Ryzen creates very nice, small, videos. For example:
5890333202 (5.5G) for the original "real-time" capture and
1173110950 (1.1G) for the handbrake encoded version.  Both are h.264/AAC encoded, though I add a vorbis audio track to the 2nd version.  The audio encoding is just stereo since the source stopped using DD 5.1 audio for DD+, which isn't supported by any of the cheapo options. To get **any** audio, I have to use stereo audio settings from the source.  I have a few players that **do not** support h.265, so I don't use that vcodec.

I've not had issues with Intel iGPUs on 4K displays. Perhaps the wrong type of physical connection is being used?  DisplayPort and VGA appear to work fine.  
[https://ark.intel.com/content/www/us/en/ark.html](https://ark.intel.com/content/www/us/en/ark.html) is the Intel Specs search page. My Intel G3258 from 2014 supports  2560x1600@60Hz over display port and 1920x1200@60Hz over VGA, but only 1080p over HDMI.  The connection type matters.

My Core i5-8250 does 4096x2304@60Hz over displayport, but only 4096x2304@24Hz over hdmi.

Perhaps we are saying the same thing?

For playback, I have raspberry pi media players.  I don't have a full computer next to the projector. We strive to keep the noise down and computers or Xbox systems are just too noisy. A raspberry pi is silent.

Glad I've had the 1030 GT 2.5 yrs now as it was still 2x the cost of what I really wanted for a GPU at $70. Mine is in a KVM host. I got a 10xx-series to extend the support period 1 more generation, in theory.

BTW, not everyone uses the GUI for package management.  I don't have an "additional drivers" option on my systems, but the **ubuntu-drivers autoinstall** accomplishes the same thing and is much easier to post in these forums as an answer. That command produces output to help folks struggling if anything bad happens, unlike using a GUI.
I don't know about that method.  'Additional Drivers' is probably the most common method.  Others:

[https://phoenixnap.com/kb/install-nvidia-drivers-ubuntu](https://phoenixnap.com/kb/install-nvidia-drivers-ubuntu)

I have a 4k tv with hdmi ports so an hdmi to hdmi connection is the preferred one.   The sff computer only has display port and vga video ports.  The dp to hdmi adapter can only get 1080p resolution in Linux.   I suppose there are tweaks and configurations (CLI, probably) but I don't want to do that.  I want to connect the computer and tv and leave it (PnP).  A discrete video card will allow hdmi-to-hdmi.   But, since I don't have one, I'm stuck with intel igpu and the limitations.

---

### Post by cryptearth on 2021-07-24
> **linuux said:**
> But, it's more powerful than the RX 550 and I need a lp card anyway since I foolishly bought a sff computer. I was desperate though and someone was selling a sff for $100.


I don't know what advantages you get with NVENC over AMD encoding but many people tend to choose the nvidia card, right? The RX 550 supports video encoding so it has more features over the GT 1030. There's only one LP choice for that card though. I can find normal, dual slot RX 550s (used and new) for various prices including as cheap as the used GT 1030s but they won't fit because they are normal height (although some are single slot and short in length). Note to everyone: don't choose sff computers unless you have measured it and know that the cards you want will fit!
Well - although I have a few cards around from both AMD and nVidia they're all too different to compare them fair to figure out if there're any diference in the hardware encoder blocks at all. So I can'T say anything about that point ...
But about the other ... limited to a not-full-atx-formfactor - I made the same mistake.
It's another reason why I original ordered the 1030: As I original used an asus a68hm-plus with the pci-e x16 slot and the x1 slot right next to each other but the x16 slot closer to the cpu I also required a single-slot card. Bonus: As it's all in a low-profile case (antec minuet 350) I was limited to a low-profile card. So the challenge was: Finding a decend enough single-slot low-profile card but with hardware encoder - the only card I was able to find which meet these specifics was some AMD Radeon Pro WX ... one of the early models - can't remember which exactly - the 2100 or 3100 or something like this. And this might had worked out - but as I had to order a card I'm not even sure would actually work the way I intended from outside of the EU (can't remember if it was from usa or china (doesn't matter - it was manufactured in china anyway)) the price tag of over 200€ made my finally opt-out of this idea.
Long story short: I found another mini-ATX board which had a slot in between - a biostar a68mde. This finally gave me the required space for using a dual-slot card - although still limited to low-profile. So I ended up with a 1650. It all worked out as nice day-trip to berlin (I live about 2h from berlin - so no big deal for a day-trip over the about 150km) into one of biggest pc-hardware stores in my local area (berlin really was the best option for me anyway as I combined it with a visit to my back then landlord) and as I had given my ASUS board and some random CPU (can'T even remember what it was) it turned out as a pretty much 1-to-1 exchange (I got about 5€+ out of the deal I spent for lunch).

If I had built it in a standard midi-tower I could had gotten away with some single-slot standard-height cards ... but going the small case route had some challenges for me.
Today, after the swap of the motherboard and added 1650 as encoder accelerator I'm happy with it ... plus: due to the 1650 it's quite a power system able to handle most games I play (as I use the 1650 right now after my big r9 290x died) - so when it gets back after a new main gpu it's available again for some 2-player LAN action.

---

### Post by linuux on 2021-07-25
> **cryptearth said:**
> Well - although I have a few cards around from both AMD and nVidia they're all too different to compare them fair to figure out if there're any diference in the hardware encoder blocks at all. So I can'T say anything about that point ...
But about the other ... limited to a not-full-atx-formfactor - I made the same mistake.
It's another reason why I original ordered the 1030: As I original used an asus a68hm-plus with the pci-e x16 slot and the x1 slot right next to each other but the x16 slot closer to the cpu I also required a single-slot card. Bonus: As it's all in a low-profile case (antec minuet 350) I was limited to a low-profile card. So the challenge was: Finding a decend enough single-slot low-profile card but with hardware encoder - the only card I was able to find which meet these specifics was some AMD Radeon Pro WX ... one of the early models - can't remember which exactly - the 2100 or 3100 or something like this. And this might had worked out - but as I had to order a card I'm not even sure would actually work the way I intended from outside of the EU (can't remember if it was from usa or china (doesn't matter - it was manufactured in china anyway)) the price tag of over 200€ made my finally opt-out of this idea.
Long story short: I found another mini-ATX board which had a slot in between - a biostar a68mde. This finally gave me the required space for using a dual-slot card - although still limited to low-profile. So I ended up with a 1650. It all worked out as nice day-trip to berlin (I live about 2h from berlin - so no big deal for a day-trip over the about 150km) into one of biggest pc-hardware stores in my local area (berlin really was the best option for me anyway as I combined it with a visit to my back then landlord) and as I had given my ASUS board and some random CPU (can'T even remember what it was) it turned out as a pretty much 1-to-1 exchange (I got about 5€+ out of the deal I spent for lunch).

If I had built it in a standard midi-tower I could had gotten away with some single-slot standard-height cards ... but going the small case route had some challenges for me.
Today, after the swap of the motherboard and added 1650 as encoder accelerator I'm happy with it ... plus: due to the 1650 it's quite a power system able to handle most games I play (as I use the 1650 right now after my big r9 290x died) - so when it gets back after a new main gpu it's available again for some 2-player LAN action.At least, you were able to use a dual slot card. 

I noticed all the gtx 1650 lp cards are dual slot.   There's quite a few.   That would be a nice option for me to have but the sff I have only has room for single slot, low profile so it's a double whammy of limitations.   The gtx 1650 lp cards are really expensive still so it's a bit of a moot point but if it ever goes back to a reasonable price, I still can't use one as an option with the computer I have.  

I guess Nvidia version 470 is out now?  How is it with your card?

---

### Post by ianwhite7 on 2021-08-12
ATI Radeon HD 2600 XT

---

### Post by kurt18947 on 2021-11-02
I'm not a gamer or high end video user so can't address the high performance cards. If I needed a video card for non-gaming use Ebay (in the US at least) has lots of Dell/AMD video card pulls including SFF. Prices in that market are about where they've been for the past few years. I've had pretty good success with ATI/AMD and Linux. There was a rough period when I had a Ryzen 3 2200G and Ubuntu 18.04 but smooth now.

---

