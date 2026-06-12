---
title: "Odd RAM Upgrade Problem"
date: 2015-03-13
forum: Hardware
---

### Post by 56es8lTI on 2015-03-13
I have a couple of older boxes I'm upgrading for use with Lubuntu.  They are actually quite capable for general use, but are badly slowed by a lack of RAM, only 512M.  I got some OEM Kensington high-density RAM modules for each which were specifically made for the AMD CPUs and SiS chipsets on these two boards, one of which will use 2G of DDR333 RAM and the other 2G of DDR400 RAM.  I successfully updated the BIOS in both boxes prior to receipt of these new modules.  Both MBs specify in their stats that they will each use two 1G RAM modules of their respective DDR speeds.

OK, the one using DDR333 RAM worked perfectly.  Stuck in both modules, it booted and ran with ZERO problems on the first try.  I'm using that box right now..  The added RAM made an **AMAZING** difference in the performance in this box, BTW.  The results far exceeded my expectations.

BUT...the one using DDR400 RAM would not boot with the two new modules installed.

It will boot and run fine with either single module installed in either slot.  It will even boot and run fine with either 1G module and the old 512M module.  It will not boot with **both** new modules.  It merely beeps on power up and that's that. :(

Because I couldn't find comparable diagnostic programs in [L]Ubuntu (if there is one, please tell me so I can install it), I booted Windows and ran Speccy for the more exhaustive specs for all this, as I posted in [this inconclusive thread]("http://forums.techguy.org/hardware/1144259-ram-upgrade-problem.html") elsewhere.

I've seen this problem in other contexts, but have not seen an actual explanation nor answer.  As far as I can tell, the BIOS settings are correct and the RAM voltage sufficient.

If anyone has any insights, I'd be grateful!

Here's the Speccy readout for the new and existing modules:

Slot #1
Type DDR
Size 1024 MBytes
Manufacturer Kingston
Max bandwidth PC3200 (200 MHz)
Part number K
Serial number 683A5A69
Week/year 09 / 33
SPD Ext. EPP
JEDEC #3
Frequency 200.0 MHz
CAS# latency 3.0
RAS# to CAS# 4
RAS# Precharge 4
tRAS 9
Voltage 2.500 V
JEDEC #2
Frequency 166.7 MHz
CAS# latency 2.5
RAS# to CAS# 4
RAS# Precharge 4
tRAS 8
Voltage 2.500 V
JEDEC #1
Frequency 133.3 MHz
CAS# latency 2.0
RAS# to CAS# 3
RAS# Precharge 3
tRAS 6
Voltage 2.500 V

OK, now here it is for the 512M module:

Slot #2
Type DDR
Size 512 MBytes
Manufacturer Kingston
Max bandwidth PC3200 (200 MHz)
Part number K
Serial number 1BFFFF04
Week/year 12 / 99
SPD Ext. EPP
JEDEC #3
Frequency 200.0 MHz
CAS# latency 3.0
RAS# to CAS# 3
RAS# Precharge 3
tRAS 8
Voltage 2.500 V
JEDEC #2
Frequency 166.7 MHz
CAS# latency 2.5
RAS# to CAS# 3
RAS# Precharge 3
tRAS 7
Voltage 2.500 V
JEDEC #1
Frequency 133.3 MHz
CAS# latency 2.0
RAS# to CAS# 2
RAS# Precharge 2
tRAS 6
Voltage 2.500 V

---

### Post by kerry_s on 2015-03-14
the only thing I can think of is it don't support 2gb

---

### Post by efflandt on 2015-03-14
You mention AMD cpu. I have a PC from 2004 with an early Athlon64 3200+ (2 GHz, 1 MB cache) and it seemed to be temperamental about RAM. Back then when I first upgraded it with a pair of 512 MB PC3200 sticks of OCZ RAM (on sale at Frys Electronics) I was having occasional issues (more so in WinXP which used more RAM than Linux, I think I was running SuSE 8 or 8.2 then) and would get some errors running memtest86+. I contacted OCZ and they sent me RAM that they guaranteed would work, and it did without any problems. Many years later I upgraded it with a pair of PNY 1 GB PC3200 and that worked without a hitch. But by then RAM was likely compatible with more different systems.

So if it seems to work with 1.5 GB try running memtest86+ or whatever the current memtest is for awhile and see if it comes up with any errors. I don't know enough about RAM spec's to tell what should work or not. We had 512 MB stick of PC2700 Crucial RAM that would occasionally blue screen in an older Pentium 1.8 or 2 GHz PC single channel RAM and I never tested it until the PC was being retired. It had failures in memtest86+, but the RAM worked without any memtest86+ errors dual channel with another brand of RAM in a different computer and lived on in that until WinXP was retired.

---

### Post by 56es8lTI on 2015-03-14
> **efflandt said:**
> You mention AMD cpu. I have a PC from 2004 with an early Athlon64 3200+ (2 GHz, 1 MB cache) and it seemed to be temperamental about RAM.[...]
So if it seems to work with 1.5 GB try running memtest86+ or whatever the current memtest is for awhile and see if it comes up with any errors.
In researching this, I came across a specific mention of that problem, but don't remember the details as it was a very different problem from the one I have.

The BIOS flash specifically enabled this CPU, a Sempron 2800+, I believe.

In all cases [above] with this box (and the other one), memtest will run until Doomsday with no errors.  The thing just won't *boot* with both of these new modules installed.

As I said, I've seen numerous mentions of this identical boot problem, but I haven't seen any useful or informative explanations of why it happens.  I'm assuming that there is some BIOS setting I'm overlooking that some expert will immediately recognize as the needed solution.

---

### Post by 56es8lTI on 2015-03-15
FWIW, here's the MB, with downloadable manual: [https://tinyurl.com/n4caqml](https://tinyurl.com/n4caqml)

---

### Post by Yellow Pasque on 2015-03-15
If i had to guess, I would say it's a limitation of Socket 754 CPU's. Look in the mobo manual on page 17 (page 39/72 of the PDF). You see that two double-rank DIMM's will only run at DDR-333 speed maximum. In theory, the motherboard should automatically drop to that speed with both the DIMM's installed, but it doesn't surprise me that the board would simply refuse to boot.

Maybe you can try booting with one DIMM, setting the BIOS to DDR333, and then trying to install the other 1 GB DIMM after you've rebooted and shut down. 
So perhaps you can get it to boot with 2GB at DDR-333, or maybe you would prefer 1.5GB running at DDR-400. Look on the bright side - either configuration is far better than just having 512MB of RAM...

---

### Post by 56es8lTI on 2015-03-16
I think you may be onto something here, but I'm not sure. :confused:

I've looked at that table until I have a headache, but I'm not sure I understand it yet.

What is "single rank" and "double rank"?  Does this refer to a **type** of module? [yes, it does: [http://en.wikipedia.org/wiki/Double-sided_RAM](http://en.wikipedia.org/wiki/Double-sided_RAM) ]

1DR + 1SR = DDR400.  1DR + 1DR = DDR333.

I think this explains why one of these modules plus the old 512M will work OK together at DDR400.

"DMM3" is a third socket not on this board and thus irrelevant to our present question, right?

I think I may be starting to see some light here! ;)

---

### Post by Yellow Pasque on 2015-03-16
> What is "single rank" and "double rank"? Does this refer to a type of module?
No, see this: [https://en.wikipedia.org/wiki/Memory_geometry](https://en.wikipedia.org/wiki/Memory_geometry)

"Usually, single-sided modules are single-rank and double-sided modules are double-rank (or sometimes quad-rank), though this doesn't have to be always the case." -- [https://en.wikipedia.org/wiki/Double-sided_RAM](https://en.wikipedia.org/wiki/Double-sided_RAM)
I'm guessing that your 1GB sticks are double-sided and double rank, so according to the table, you can only run at DDR333 regardless of what command rate you use (1T or 2T).

> "DMM3" is a third socket not on this board and thus irrelevant to our present question, right?
Correct, you can consider it empty.

---

### Post by 56es8lTI on 2015-03-16
> **Temüjin said:**
> I'm guessing that your 1GB sticks are double-sided and double rank, so according to the table, you can only run at DDR333 regardless of what command rate you use (1T or 2T).

Yeah, except in the case of singly using one of these double-rank modules or combined with a single-rank module, as I have when I use the old 512M module.  Together, they work as DDR400 (see Speccy, above), and that seems to be supported by the chart data in the manual.

However, I don't see an option in the BIOS to run these two 1G DDR400 modules at DDR333, **but I certainly may be missing something**.  I would prefer 2G DDR333 if I could find a setting, but it would require a setting change somewhere, as they won't boot at all otherwise.

Any thoughts on this?

It looks like what I may have wound up with is a roundabout (but solid) 1.5G upgrade rather than a 2G upgrade, but at the price I can live with it.

---

### Post by Yellow Pasque on 2015-03-16
In the BIOS, look at Advanced Chipset Setup -> DRAM Configuration. You have to change "DDR Timing Setting By" to 'Manual' and select DDR333 (or 167MHz).

---

### Post by tgalati4 on 2015-03-16
Try a new power supply.  A little bit of AC noise could upset the RAM timing causing the new RAM sticks to fail.  It could also be failing capacitors on the motherboard--any bulging or leaking capacitors?  If this was a new motherboard and power supply, then I bet the RAM sticks would work as the specifications suggest.

Upgrading old hardware with RAM can give it new life, but also create new problems.

---

### Post by Yellow Pasque on 2015-03-16
> If this was a new motherboard and power supply, then I bet the RAM sticks would work as the specifications suggest.

AMD's Socket 754 specs say otherwise. If other sticks of RAM work at DDR400, bad power supply seems very, very, very unlikely, as does bad caps (though visual inspection of caps on boards from this era is a very good idea regardless). If you google a bit, you'll see other people report that two double-sided sticks won't run at DDR400 on S754. They report fallback to DDR333, but like I said, if the mobo simply won't boot with an unsupported RAM configuration, that doesn't surprise me given how finicky mobos can be with RAM.

I've got a triple core Phenom II, and I see a lot of people with the same model saying the fourth core unlocks. Mine doesn't (even with extra CPU voltage). That doesn't mean I have a bad PSU or something else wrong with my system...

---

### Post by 56es8lTI on 2015-03-16
> **Temüjin said:**
> In the BIOS, look at Advanced Chipset Setup -> DRAM Configuration. You have to change "DDR Timing Setting By" to 'Manual' and select DDR333 (or 167MHz).

I'll look at that.

---

### Post by Yellow Pasque on 2015-03-16
It's the memory controller, which is built directly into the CPU for Socket 754 CPU's.
That's probably why that table in the mobo manual mentions a third RAM slot when your board doesn't have one. I'm pretty sure ECS just copied the table from AMD docs since it applies to Socket 754 CPU's in general.

---

### Post by 56es8lTI on 2015-03-16
> **Temüjin said:**
> bad power supply seems very, very, very unlikely, as does bad caps (though visual inspection of caps on boards from this era is a very good idea regardless). 

It is:  Act One in this slapstick upgrade comedy -- days before the RAM arrived -- was a failure to boot followed by a doomsday stench that quickly pervaded the entire house for a full day thanks to the old AGP card's blown electrolytics.  Blown electrolytics are even more entertainment at high voltage. :shock:

The caps on the MB look fine.

---

### Post by Mike_Walsh on 2015-03-16
I run the Athlon 64 myself..... the socket 939 version (I think from the year following yours - 2005). It's on an MSI mobo (an MS-7184; which you'll not find listed by MSI, as it was made under contract to HP, just after they took Compaq over). Fellow owners will know it as the 'Amethyst M'.

This board has 4 DDR1 slots. It will run with 1 slot in use, 2 slots, OR 4 slots. It will NOT run with 3. I found this out the hard way, before I found the manual for it online..! Depending on the slot usage, it will either run at full speed, DDR400 (PC3200), OR at DDR333 (PC2700).....and also depending on whether or not you run it in dual-channel mode.

[ATTACH=CONFIG]260671[/ATTACH]

It's all determined by the HyperTransport memory controller, which, as has been already stated, is on the CPU die on these chips; the Athlon 64 was the very first production CPU to do so. Nowadays, of course, it's standard practice; but back in 2003/4, AMD were really breaking new ground with this feature.

I was told many years ago to avoid 'high-density' RAM like the plague, if you intended to use it in a home PC. It was always intended for use in servers, along with the supported error-correcting feature.


Regards,

Mike. :)

---

### Post by 56es8lTI on 2015-03-16
> **Mike_Walsh said:**
> 
I was told many years ago to avoid 'high-density' RAM like the plague, if you intended to use it in a home PC.

Yes, they won't work **at all** with many chipsets/CPUs.  However, this batch was apparently made specifically for these chipsets and as a result they work perfectly (according to hours of memtest so far) -- except for this interesting CPU oddity that apparently has nothing to do with either the RAM or the MB themselves.

So, it looks as though nothing is actually broken, defective or amiss here -- just obscure.  

I'm going to thank everyone who's helped and tagged this solved.

---

### Post by Yellow Pasque on 2015-03-16
So did you get the 2GB running at DDR333 or did you decide to go with 1.5GB at DDR400?

I'm wondering which one would be faster. I guess it depends on whether you regularly use more than 1.5GB of RAM (although that's not hard to do these days, especially with web browsing).

---

### Post by 56es8lTI on 2015-03-17
> **Temüjin said:**
> So did you get the 2GB running at DDR333 or did you decide to go with 1.5GB at DDR400?

I'm wondering which one would be faster. I guess it depends on whether you regularly use more than 1.5GB of RAM (although that's not hard to do these days, especially with web browsing).
I haven't messed with it at this point because I don't know which would be better, either.  I'll probably try it at DDR333 later this week, as I have other pressing stuff keeping me off these boxes at the moment.  My main goal here was to **understand** what was happening, which thanks to your careful eye I now do. ;)

I have some more immediate hardware issues with these boxes, like trying to decide how to go with the video on the one with 2G active, whether to allot much more of its new RAM to use its internal video or try to dig up a better old AGP card to replace the one that blew.  I'm just gradually trying to see how far I can optimize these old boxes without a lot of outlay of cash, largely out of curiosity.  At $7.80, shipped, for 2G of RAM the performance improvement was quite astonishing so far.  

There are also some Linux hardware compatibility problems (?) to sort out, "errors" that don't seem to be impeding any actual function.  To get all this ironed out (if it even needs to be), or at least better understood, would give me a good deal of satisfaction.  

Some of us simply never outgrow obsessive curiosity. :D

---

