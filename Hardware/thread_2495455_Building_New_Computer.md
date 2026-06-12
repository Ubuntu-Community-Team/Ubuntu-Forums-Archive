---
title: "Building New Computer"
date: 2024-02-20
forum: Hardware
---

### Post by daniell59 on 2024-02-20
My old computer finally gave up the ghost. The Asus P5Q Pro served me well for 15 years. I would appreciate suggestions for my new build.
It must be Linux compatible. I am not a gamer, and don't plan to be.
I am thinking of the Ryzen 5 8600G. I need to purchase everything except for the case and the power supply.

Thanks

---

### Post by TheFu on 2024-02-20
Budget?

I usually start out with a $200 CPU, but I'm sensitive to the "value" and might spend a little less or a little more if the performance numbers for a "good value" CPU are right.
[https://www.cpubenchmark.net/cpu_value_available.html](https://www.cpubenchmark.net/cpu_value_available.html)  So, right now, the best "performance for the buck" is a Ryzen 5 5500. It doesn't have any GPU, it is AM4, which means you'll need an AM4 motherboard.  Supplies of the popular versions of those motherboards are becoming tight, so perhaps the AM5 premium would be worth it. Only you can decide.

Using passmarks to compare CPU performance is better than nothing. Sure it is flawed, but any CPU within 500 passmarks is effectively the same level of performance.

With Ryzen AM5 or AM4 sockets, we gain access to an entire line of possible CPU upgrades.  AM4 is at the trailing end of new CPUs. AM5 is just starting.

AM5 requires DDR5, which is also at a premium, so don't expect $50 to cover your RAM desires.  Double that.  DDR4 is finally cheap.  That's a consideration.

After I pick the CPU, then I head over to PCPartpicker to get ideas for the motherboard and other stuff.  I'm partial to Asus and MSI.  Be certain to download the motherboard manual to learn about odd things - like that PCIe slot 3 is disabled if you install 2 m.2 NVMe drives.  Or the 6 SATA ports, if used, prevent the 2nd m.2 slot from being used. Stuff like that.

Also I actively avoid Realtek network chips. I've been burned too many times and the $20 extra it costs to get an Intel NIC on the motherboard so I don't have driver or performance issues is well worth the cost.  Intel "just works".  These forums are full of people with Realtek having problems.

My last build was a Ryzen 5600G (I wanted to avoid a separate GPU).  The included iGPU is better than a low-end nVidia which runs ~$100 and it will use less power, and they support video transcoding in hardware - which doesn't show up in CPU load at all, if you do anything like that.  So, while the "G" Ryzen CPUs (AMD calls then APUs), aren't often a great value, just take $70 off the price and run your cost calculations again.

What would you actually do with an 8600G and the 25000 passmarks? [https://www.cpubenchmark.net/cpu.php?cpu=AMD+Ryzen+5+8600G](https://www.cpubenchmark.net/cpu.php?cpu=AMD+Ryzen+5+8600G)
It looks like $230 is the current price.   That Ryzen 5500 is $85 for 19000 passmarks.  A linear price says that 25K passmarks should cost $112. Add $70 for the iGPU and $182 is the "deal price".    In short, that CPU is NOT A VALUE at the current price.  I'd pass.

If I needed a computer today because I didn't have one, I'd buy the best used computer I could get for $80 while I waited up to a year for AM5 prices to drop, if I would only accept AM5.

For people who don't plan to upgrade their CPU later, Intel CPUs can be an excellent value. The Core i5-13400F [https://www.neweggbusiness.com/Product/Product.aspx?Item=9SIA4N9HRN4308](https://www.neweggbusiness.com/Product/Product.aspx?Item=9SIA4N9HRN4308)  is about $136 less, has an iGPU and still provides 25K passmarks. They have a non-"F" version for $156.
Of course, intel motherboards change faster than a 4 month old in diapers, but if you use a computer for 10+ yrs, that doesn't matter to you.

You may need a new monitor.  Current GPUs/iGPUs have DisplayPort video outputs.  VGA is long dead. Some may or may not have HDMI.  I was hit with this issue myself.  I ended up getting a new KVM switch - which isn't nearly as good as my old VGA one, except it supports 4K monitors. I don't have any 4K monitors, but I was planning ahead with the KVM purchase.  Someday, I'll get a 4K monitor, probably.

So, what's your total budget and the budget for each major component?

---

### Post by oldfred on 2024-02-20
I know TheFu prefers AMD, but I have always used Intel. But I do keep systems for many years and do not need fastest system. I do not game.
I so not use separate video card as CPU chip with video is more than adequate and lower in cost than CPU without video & separate video card.

My full build in 2017 needed new power supply. Specs said old supply was same standard, but system would not boot. Went to MicroCenter which was nearby and it booted with their supply with out issue. 

Regretted not getting new Case. Wanted USB3 port on front, but old case was only USB2 and connectors from motherboard to case was not the same. Only power switch really worked. Now if building system I would want USB-C ports. I now would buy smaller case, but some require a more expensive small power supply.
 [https://www.tomshardware.com/best-picks/best-mini-itx-pc-cases](https://www.tomshardware.com/best-picks/best-mini-itx-pc-cases)

Also made the mistake of incompatible video. Old monitor was VGA & DVI in, motherboard was HDMI or Displayport out. Used old nVidia card that it turned out had lower video specs than Intel CPU's video. Then found adapter cable to go from Motherboard to monitor.

NVMe with M.2 is now lower in cost, so if you want a fast booting system, that is worthwhile.

---

### Post by daniell59 on 2024-02-20
Thanks to all for your informative replies. For the short term I resurrected an even older computer than the one that just died. I moved the SSD and reinstalled Ubuntu 22.04. I did a dual boot on that drive with the already installed OS and the freshly installed one. I was surprised that the OS that was running on the previous one would run on the resurrected one. The previous computer was Intel and this one is AM2.

---

### Post by TheFu on 2024-02-20
> **daniell59 said:**
> Thanks to all for your informative replies. For the short term I resurrected an even older computer than the one that just died. I moved the SSD and reinstalled Ubuntu 22.04. I did a dual boot on that drive with the already installed OS and the freshly installed one. I was surprised that the OS that was running on the previous one would run on the resurrected one. The previous computer was Intel and this one is AM2.

For the most part, x86-64 CPUs are all compatible unless you specifically set some programs to use extensions for a specific chip.  Virtualization tools commonly allow that feature. The installed software usually tests (or queries) the OS for specific extensions that are supported that it knows how to use.  If you care, you can see the list of CPU extensions using the **lscpu** command - check the "Flags" list.

I've moved virtual machines from Intel to AMD.  Once I forgot to change the CPU model inside one VM to match the CPU of the host and it refused to boot.  I'm embarrassed to say how long it took me to figure that one out, but it was more than 2 hrs.

---

### Post by TheFu on 2024-02-22
[https://www.phoronix.com/review/intel-14100-14500-amd-ryzen](https://www.phoronix.com/review/intel-14100-14500-amd-ryzen) - Intel Core i3 14100 / i5 14500 vs. AMD Ryzen 5 8500G / 8600G In 500+ Benchmarks just published.  Results are mixed with the 2 Ryzens and Core i5 trading top spots in different benchmarks.  Yes, the 8500G is faster than the 8600G in some workloads.  The Core i5 is faster than both in some workloads.

What I find really interesting is the prices/performance.  I like to make a graph when I'm looking for a CPU with price vs performance.  Often, they are not linear as we would hope.  Pricing sometimes is off and that's when we can find really great deals.

---

### Post by him610 on 2024-02-22
@oldfred
> Regretted not getting new Case. 
I normally prefer building mini-ITX systems, but on my most recent build, I decided to re-use an existing micro-ATX case. To make a long story short, I wound up having to buy a new case anyway. Since I had already bought the micro-ATX motherboard, I had to settle for a computer case about twice the size of one of my mini-ITX cases.
The one advantage (IMHO) of the micro-ATX case over the mini-ITX is the extra room inside of the case. That's it just one advantage. Others may disagree.
Added: After some thought, the larger ATX/micro-ATX cases and motherboards have the advantages of hosting more drives (HDD/SSD) and more card slots for peripherals.

---

### Post by TheFu on 2024-02-22
I haven't bought a new case since around 2002.  The computers inside those cases have changed at least 3 times.  They have thumb screw access to get inside (I bought a 50 pak of those screws), which makes a huge difference.  All are mid-tower, but one is extra wide from a dual CPU system I had in the late 1990s, well before CPU cores existed.

I like having 6 HDDs inside the same case and sharing storage on the LAN between both systems.  I have a "spare", slow, Core i5-750 that isn't powered on. It is handy when I need to connect outside my core network and do things that may not be exactly safe.  It can be a router, if I need to take my main WAN router out of service.  It is old enough to have issues with USB3 devices.  The internal bus just wasn't made for USB3 bandwidth.

I have 2 ITX cases too.  They were for media center system, which have long been replaced with Raspberry Pi systems that are faster and more flexible than the ITX motherboards supported.  Plus the PSUs that came in those systems were far too loud.  I replaced one with a PicoATX 65W power supply, which was silent and had an external brick. Nothing making noise inside the case except the CPU fan on the AMD E-350 APU.  I don't even count that computer as working that E-350 is so very slow with just 400 passmarks.   A good-enough desktop really needs 6000 passmarks these days.  Should be able to build one for about $150, reusing a case.

---

### Post by daniell59 on 2024-02-23
I have two old Lian Li aluminum ATX cases. Many of the fans are 80mm and can't be upgraded to 120mm. I wonder if that will provide for sufficient cooling with upgraded components. both cases have a removable MB tray. Everything comes off with thumb screws. On both cases the front panel is held on by tape. The plastic clips have rotted away. Discarding the cases would be like throwing out an old sick dog.

---

### Post by TheFu on 2024-02-23
> **daniell59 said:**
> I have two old Lian Li aluminum ATX cases. Many of the fans are 80mm and can't be upgraded to 120mm. I wonder if that will provide for sufficient cooling with upgraded components. both cases have a removable MB tray. Everything comes off with thumb screws. On both cases the front panel is held on by tape. The plastic clips have rotted away. Discarding the cases would be like throwing out an old sick dog.

My systems have 1 extra 80mm case fan, beyond what the PSU and other components already have.  Never had any heating issues.
They both have a 120mm fan that pulls air over the 4 drive caddy inside each system, but the drive cage came with those fans.  After about 1 yr, the cheap fan breaks and I replace it with a 120mm Noctua fan and set it too spin very slow - around 1200rpm so it is quiet. Before I put drive cages into my systems, there weren't any extra fans.

```
~/SMART$ egrep -i Tempera smart.2024-02-19*
smart.2024-02-19.nvme0n1:Temperature:                        38 Celsius
smart.2024-02-19.nvme0n1:Temperature Sensor 1:               38 Celsius
smart.2024-02-19.nvme0n1:Temperature Sensor 2:               54 Celsius
smart.2024-02-19.sda:194 Temperature_Celsius     0x0002   162   162   000    Old_age   Always       -       37 (Min/Max 24/50)
smart.2024-02-19.sdb:194 Temperature_Celsius     0x0002   176   176   000    Old_age   Always       -       34 (Min/Max 19/49)
smart.2024-02-19.sdd:190 Airflow_Temperature_Cel 0x0022   061   049   045    Old_age   Always       -       39 (Min/Max 36/44)
smart.2024-02-19.sdd:194 Temperature_Celsius     0x0022   039   051   000    Old_age   Always       -       39 (0 21 0 0 0)
smart.2024-02-19.sde:194 Temperature_Celsius     0x0002   166   166   000    Old_age   Always       -       36 (Min/Max 20/50)
smart.2024-02-19.sdf:194 Temperature_Celsius     0x0002   144   144   000    Old_age   Always       -       45 (Min/Max 18/54)
smart.2024-02-19.sdg:194 Temperature_Celsius     0x0002   141   141   000    Old_age   Always       -       46 (Min/Max 21/55)
smart.2024-02-19.sdh:194 Temperature_Celsius     0x0022   113   098   000    Old_age   Always       -       39
```

And on the other system:
```
~/SMART$ egrep -i Tempera smart.2024-02-20.*
smart.2024-02-20.nvme0n1:Temperature:                        40 Celsius
smart.2024-02-20.nvme0n1:Temperature Sensor 1:               40 Celsius
smart.2024-02-20.nvme0n1:Temperature Sensor 2:               45 Celsius
smart.2024-02-20.sda:194 Temperature_Celsius     0x0022   107   091   000    Old_age   Always       -       45
smart.2024-02-20.sdb:194 Temperature_Celsius     0x0022   117   108   000    Old_age   Always       -       30
smart.2024-02-20.sdc:194 Temperature_Celsius     0x0002   181   181   000    Old_age   Always       -       33 (Min/Max 19/43)
smart.2024-02-20.sdd:194 Temperature_Celsius     0x0002   176   176   000    Old_age   Always       -       34 (Min/Max 24/49)
smart.2024-02-20.sde:194 Temperature_Celsius     0x0022   116   106   000    Old_age   Always       -       31
```

Mostly chill.  The NVMes run hotter and drives that don't have a fan pulling air over them run a little hotter, but not too hot.  Most recommendations suggest 25-50 degC. A few peaks above those temperatures aren't to be worried about.

---

### Post by Yellow Pasque on 2024-02-25
> **daniell59 said:**
> Many of the fans are 80mm and can't be upgraded to 120mm. I wonder if that will provide for sufficient cooling with upgraded components.

I wouldn't worry about it. If you're going to build with an efficient 65W chip like the 5600G or 8600G on a Bx50 mobo, you can probably get away without case fans as long as the case has decent vents. I've got two 5600G systems and I don't have any case fans. In fact, I can't remember the last time I built with a case fan - I want to say 10-15 years ago.
Also, 80mm fans can move as much air as a slower 120mm fan (but of course, they make more noise doing it).

And yeah, I keep reusing old cases (even if the panels don't want to stay on) too.

---

### Post by daniell59 on 2024-02-26
I am still deciding whether to go with the 5600G or the 8600G. My concern with going with the 5600G is component availability in the future. My concern with the 8600G is higher prices and whether it will work well with Linux.

---

### Post by ninoivanov on 2024-02-26
Look at the other replies here when something goes **really** wrong - and decide yourself, do is "this" ready for prime-time or not.

---

### Post by Yellow Pasque on 2024-02-26
> **daniell59 said:**
> I am still deciding whether to go with the 5600G or the 8600G. My concern with going with the 5600G is component availability in the future. My concern with the 8600G is higher prices and whether it will work well with Linux.

The 8600G should work fine with Ubuntu 23.10 or later: [https://www.phoronix.com/review/amd-ryzen5-8600g](https://www.phoronix.com/review/amd-ryzen5-8600g)
Exactly what components are you worried about in terms of future availability? I don't see it as an issue. The only thing with 5600G is that there won't be any newer gen CPU upgrades to Socket AM4, but I don't think that would concern someone who was still using a 15 year old computer as their "daily driver".

---

### Post by TheFu on 2024-02-26
> **Yellow Pasque said:**
> The 8600G should work fine with Ubuntu 23.10 or later: [https://www.phoronix.com/review/amd-ryzen5-8600g](https://www.phoronix.com/review/amd-ryzen5-8600g)
Exactly what components are you worried about in terms of future availability? I don't see it as an issue. The only thing with 5600G is that there won't be any newer gen CPU upgrades to Socket AM4, but I don't think that would concern someone who was still using a 15 year old computer as their "daily driver".

AM4 will be around as long at AM3 was around.  Parts for all computers become constrained over time.  I had a job where I was tasked to keep some very old computers running for decades.  When we couldn't to it anymore, the service that computer provided to clients was shutdown.  Finding 2GB HDDs (the BIOS didn't support larger) was very hard.  Motherboards on those systems were built to last forever, but some things would die after 15 yrs and I'd have to search computer junk yards world-wide for parts.  There's a huge set of 2nd market dealers out there. Not so much for PCs, but for UNIX systems, they are happy to provide 20MB SCSI-2 HDDs for $600, until they don't have anymore.

For AM4, with a 5600G (there are other "G" models), the upgrades will be CPU only.  I doubt DDR4 RAM will get much cheaper, so if you might need it, fill the slots today with the largest amount of RAM you may need in the future.  MicroATX might only support 32G-64G.  Full-ATX might stop at 64G, but there are models that support 128GB.  I have to say, my 5600G aren't RAM or CPU bound when doing normal workloads.  It is only when I insist on doing software-based video transcoding that the CPU and all cores get pegged.  If I use the iGPU for video transcoding, the CPU is barely used.  HW transcoding results for the same output files just isn't as good and there are limited controls over variable bitrates per frame.  To get the same quality output, about 50% more storage is needed with hardware transcodes compared to CPU-based transcodes.  Also, HW transcodes are 3-6x faster than CPU transcodes.  So, for archived video content, I'll have the CPU do the transcoding. For watch-once stuff, I'll use higher bitrates and accept that the output file size will be larger.

For normal use without heavy workloads, a 5600G would be overkill.  A B550 motherboard should support Ryzen 2xxx - 5xxxx AM4 socket CPUs.  That's a pretty wide range of performance and costs.  All use DDR4 RAM, so it comes down to picking the CPU that gets the required performance.  For typical desktop stuff, I didn't see any real CPU performance difference between 13000 passmarks (2600) and 19000 passmarks (5600G).  I'm still amazed at the performance of a Core i5-8250U laptop, which was around 6000 passmarks last time I checked.  

The "passmark" benchmark seems to change every year, to older CPU numbers drop over time.  My first Chromebook (Acer C720 w/ Celeron 2995u) had a passmark rating of 1500, which wasn't fast, but it was sufficient to do desktop stuff.  Today, that CPU passmark-2024 is 872.  The CPU isn't any slower. It is the benchmark that has changed.

---

### Post by daniell59 on 2024-02-26
My present computer and the one that just died used DDR2 memory. The 4 GIGs that I have is inadequate. There is no point is upgrading it. What memory that is available is expensive for what I would be getting.

---

### Post by TheFu on 2024-02-26
> **daniell59 said:**
> My present computer and the one that just died used DDR2 memory. The 4 GIGs that I have is inadequate. There is no point is upgrading it. What memory that is available is expensive for what I would be getting.

About 3 yrs ago, I gave away all my extra DDR2 sticks to someone local.  He only wanted a few, but I needed to get all of them out of here, so I forced him to take all of them. The static bag had at least 10 sticks, maybe 20.

I probably have 50+GB of DDR3 RAM here in MB+CPU+RAM setups looking for a good home. In general, each of them had 8GB, if not 16GB of RAM.  The shipping costs more than the MB+CPU+RAM is worth, sadly.  Anyone local can buy me a $15-$25 meal and we'll call it even. No shipping offered.  Systems with a G3258 and Core i5-750 CPUs remain.  The Core i5 requires a GPU.  The G3258 has an iGPU, but the Realtek NIC on the motherboard is flakey. I can throw in a low-quality SMC GigE NIC, if that's wanted. Those NICs never did better than 250Mbps, even though they claimed to be GigE.

I do have 16GB of DDR4 3200Mhz RAM that will likely never be used here too. 2x 2x8GB matched pairs.  I started with those in my Ryzens. Adding an additional 16GB to a system even with the same manufacturer and part number resulted in unmatched sets so the chip timings were far enough off to make unstable systems until I slowed the RAM settings down to 2600Mhz in the BIOS.  After running stable for about a year, DDR4 prices dropped and I did some upgrades, including RAM.  Nothing wrong with the 2x8GB sets - they work great, individually, but few people seem to want that amount of RAM anymore, so I'm likely stuck with it.

Too many parts around here, but not enough to make a full system since I reuse PSUs and cases.

---

### Post by daniell59 on 2024-02-27
While we are on the topic of computer builds, I could use advise on the following. I have a relatively new unused computer case. Rosewill Challenger S. On my future build I would like to add a USB C port to the front of the case. Any suggestions on how I can do this.

---

### Post by TheFu on 2024-02-27
> **daniell59 said:**
> While we are on the topic of computer builds, I could use advise on the following. I have a relatively new unused computer case. Rosewill Challenger S. On my future build I would like to add a USB C port to the front of the case. Any suggestions on how I can do this.

What I did was to buy a front panel USB3 dodad.  They come in sizes for the old 3.5inch floppy disk position or a larger 5.25inch HDD slot with lots of media adapters (35-in-2), USB2, USB3, and even an eSATA port.  I would warn you that all those USB2 devices will slow down booting - perhaps for 3 minutes, if you have any USB booting enabled at all.

[https://www.amazon.com/GRAUGEAR-Internal-Required-Computer-G-MP01/dp/B09XV6XDLJ](https://www.amazon.com/GRAUGEAR-Internal-Required-Computer-G-MP01/dp/B09XV6XDLJ) is a little expensive, but should provide the idea.
Also, I have a 6-10ft long USB3.2 extension cable that is connected in the back (also USB 3.2 port) but sits near my monitor when I'm using an SSD-based USB3.2 storage device.

I have something like this too - [https://www.amazon.com/20%C3%9717%C3%976-5-25inches-Multifunction-Internal-Dashboard/dp/B0CDW16HQV](https://www.amazon.com/20%C3%9717%C3%976-5-25inches-Multifunction-Internal-Dashboard/dp/B0CDW16HQV) , not the same, but similar.  I only have audio, 2 USB3, and eSATA connected. It has 4 USB2 ports and 2 card readers which I used to have connected, but unplugged because checking every possible USB2 device at boot time was really, really, really, really, really, really, really, really, really, really, really, really, slow.  I may have understated how slow it was. ;)

For lots of other options, look for "front panel header".
Also, make certain the motherboard has internal ports for what you need to connect.  My B450 has 2 USB3 internal ports at the front of the motherboard, which plug directly into the USB3 front panel - no hub - which can be very important for compatibility of some devices.  Not all USB devices work through USB hubs.

---

### Post by Yellow Pasque on 2024-02-27
> **daniell59 said:**
> Rosewill Challenger S

It has 5.25" slots, so something like this: [https://www.newegg.com/p/2VR-00G6-000H9?Item=9SIAERNBKW1664](https://www.newegg.com/p/2VR-00G6-000H9?Item=9SIAERNBKW1664)
As Fu said, be careful with the headers. Some use 19-pin (sometimes called 20-pin though one of the pins is unused) internal USB 3.0 connectors. Your motherboard would need two of those connectors if you're going to use one for the USB 3.0 ports already on the case. Some need a type-c header on the motherboard. The one I linked to uses a USB 3.0 connector along with a SATA power plug to power the type-c port.

---

### Post by daniell59 on 2024-03-02
I have been looking at different 5.25 inch front panel hubs for my old case that only has USB 2.0. I have seen hubs that include USB C along with microphone and speaker jacks. How important is it for the USB C to be powered? Does the MB provide for adequate power?

---

### Post by TheFu on 2024-03-02
> **daniell59 said:**
> I have been looking at different 5.25 inch front panel hubs for my old case that only has USB 2.0. I have seen hubs that include USB C along with microphone and speaker jacks. How important is it for the USB C to be powered? Does the MB provide for adequate power?

Do you want to charge anything with the connection?  Otherwise, it will be enough for an SSD USB, but perhaps not enough for a spinning HDD. Spinning HDDs always need to have external power to get the any performance. USB isn't meant to power a 2.5in or 3.5in spinning HDD.  If it works, performance usually is much, much, lower.

---

### Post by Yellow Pasque on 2024-03-02
> **daniell59 said:**
> I have been looking at different 5.25 inch front panel hubs for my old case that only has USB 2.0.
Wait. What case and motherboard are you talking about? The Rosewill Challenger S has one front USB 3.0 port from what I see. This is getting confusing. You started out talking about building a new system, and now you are talking about adding Type-C to a current system or to a new system in the Challenger S?

> How important is it for the USB C to be powered? Does the MB provide for adequate power?

The motherboard will only provide adequate power with a Type-C header or some kind of external power source. If you only connect the 19/20 pin USB data cable, the Type-C port may function as a basic USB port, but don't quote me on that. As Fu said, it's not going to charge anything.

---

### Post by daniell59 on 2024-03-02
Thanks for your informative replies. It is more clear to me now.

---

### Post by daniell59 on 2024-03-03
I should have be more clear. I have 3 cases. Two Lian Li and one Rosewill. One of the Lian Li cases is the home for a very old Bios Star motherboard. This case front panel is limited to two USB 2.0 ports. The other Lian Li case has two USB 2.0 ports, an audio port, mike port and a 1394 port. I am still deciding the following. Should I go AM4 or AM5? Should I add ports to the old Lian Li case or use the newer Rosewill Challenger S? What I like most about the Lian Li case is the removable motherboard. Please forgive me for my inane rant.

---

### Post by TheFu on 2024-03-03
All valid considerations.

> This case front panel is limited to two USB 2.0 ports. 

That's just if you use the built-in ports.  Nothing says the new motherboard must connect to them at all.  I have a case with ports like that on the bottom front, but with my Ryzen build, I completely ignore those and put in a fancy 5.25in port front-panel (as described previously) below my 4x drive cage.

---

### Post by him610 on 2024-03-03
On one of my computers with only two front USB 2.0 connections, I bought a short extension cable, plugged it into one of the USB 3.0 ports on the motherboard in rear of the case, and just dangled it over the top of the case. It was an economical, practical way to get upgraded USB port to front of case. I only need to look for it as both cable and case are black.

---

