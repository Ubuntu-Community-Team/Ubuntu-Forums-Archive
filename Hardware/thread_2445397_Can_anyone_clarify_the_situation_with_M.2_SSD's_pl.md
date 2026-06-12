---
title: "Can anyone clarify the situation with M.2 SSD's please?"
date: 2020-06-13
forum: Hardware
---

### Post by jcdenton1995 on 2020-06-13
So I know this isn't specifically an Ubuntu question, but I'm building my first PC soon and will be installing Ubuntu on it so there is that...

I've been researching online in preparation for selecting my parts and I'm a good way in but there's this question of M.2 drives that's driving me insane! Mainly because a lot of the material online is contradictory of worded sloppily.

So M.2 form factor devices are designed to support the SATA, USB 3.0 or PCIe bus, does this mean that a given M.2 device could potentially use either of these 3 busses, with the actual bus used depending on which bus the motherboards M.2 socket offers / UEFI settings? or is it the case that a particular M.2 device would only support that bus which was appropriate to the type of device it was (e.g an NVMe M.2 SSD would use PCIe, while a non NVMe device would use SATA) but that the statement itself actually simply means the form factor offers vendors flexibility to implement support for one of the 3 busses.

My second question is, are all M.2 SSD's, that work over PCIe, NVMe devices? In other words is it the case that the sole reason an M.2 SSD works over PCIe is to enable the use of NVMe? or do there exist non NVMe capable M.2 PCIe SSD's? (I'm aware there were PCIe SSD's that predate NVMe and used another protocol, but I'm speaking specifically about M.2 PCIe SSD's)

And my final question is, is it possible for an M.2 socket to be connected to more than one type of bus?

If anyone could help clear these things up that would be really great!

---

### Post by CatKiller on 2020-06-13
M.2 is the form factor. Not all M.2 devices are SSDs: M.2 WiFi devices are also fairly common.

NVMe is a logical interface for storage devices connected over PCIe. It allows for addressing in parallel rather than the Serial ATA. Not all NVMe devices are M.2: you can just plug some of them into a PCIe slot. 

Which connections are supported across a particular M.2 interface is down to the manufacturers of the devices on each side. There are M.2 SSDs that can only use SATA. A motherboard having one M.2 slot that can only do SATA, and a second slot that can do both SATA and PCIe, is a common arrangement. Sometimes the PCIe lanes will be shared with another socket on the motherboard, so using the lanes for an SSD means that fewer are available for that other slot. 

SATA Express is the interface that supports both PCIe and SATA. By supporting SATAe SSD makers can use whichever interface happens to be available.

Because of all the cross-compatibility, and signalling negotiation, the devices will all *work*. For the fastest speed you will want an NVMe device in something that can use PCIe lanes that aren't shared with anything else.

---

### Post by jcdenton1995 on 2020-06-13
> **CatKiller said:**
> There are M.2 SSDs that can only use SATA.

Are there also M.2 SSDs that can selectively use SATA or PCIe, depending on what the socket supports?

 > A motherboard having one M.2 slot that can only do SATA, and a second slot that can do both SATA and PCIe, is a common arrangement. Sometimes the PCIe lanes will be shared with another socket on the motherboard, so using the lanes for an SSD means that fewer are available for that other slot. 

I see, so that must mean that the motherboard manages dynamically which lanes, and how many, are allocated to various peripherals based on what you have plugged in?

> SATA Express is the interface that supports both PCIe and SATA. By supporting SATAe SSD makers can use whichever interface happens to be available.

When you say SATA Express is an "interface", does this mean a logical interface, as in a protocol similar to NVMe, that the devices manufacturer implements to allow it to function over both PCIe and SATA?  

Sorry for the barrage of questions, this is my first PC build and it can sometimes feel like trying to unpick a Gordian knot!

---

### Post by Dennis N on 2020-06-13
> Are there also M.2 SSDs that can selectively use SATA or PCIe, depending on what the socket supports?
No. An m2 SSD drive works with one of these only.

Check specs to see what the motherboard m2 connector supports - SATA, NVMe or either.  The PCIe drives are often labeled 'NVMe SSD' on the box.  I have a m2 SATA drive plugged into the single m2 connector on this computer (built in 2014) because they were the first drive products available to use the connector. Later, NVMe m2 drives came along. Rather than replace the m2 SATA drive, I used an adapter to add an NVMe drive. The adapter card plugs into a PCIe x16 slot. 

I think SATA express is now pretty much abandoned by motherboard manufacturers?

---

### Post by CatKiller on 2020-06-13
> **jcdenton1995 said:**
> Are there also M.2 SSDs that can selectively use SATA or PCIe, depending on what the socket supports? 

Yes, that's what the SATAe standard was for. Rather than just doing "SATA, but faster," they got aligned with PCIe. So if an SSD maker had already designed their chip to use SATA, that will still work with the new standard. If they're going all in on PCIe, that will work, too. If a motherboard runs out of PCIe lanes, the SSD can still work over SATA. 

> I see, so that must mean that the motherboard manages dynamically which lanes, and how many, are allocated to various peripherals based on what you have plugged in? 

I think it mostly happens at boot time, but yes, connections are made based on which lanes are available. Hotplugging is supported by at least some of these things. 

> When you say SATA Express is an "interface", does this mean a logical interface, as in a protocol similar to NVMe, that the devices manufacturer implements to allow it to function over both PCIe and SATA?
Yep, that's the idea. It happened before NVMe and M.2 were finalised, I think, but it meant that all the fiddly stuff for negotiating connections had already been done.

Device development takes a long time, inventory is expensive, and rollout only happens gradually. By aligning existing standards (SATAe) and then pushing them forwards in a backwards-compatible way (NVMe) no one gets lumbered with warehouses full of obsolete gear.

---

### Post by jcdenton1995 on 2020-06-14
> **Dennis N said:**
> No. An m2 SSD drive works with one of these only.

Yes I believe your right about SSDs that are specifically in the M.2 form factor only supporting one physical bus interface or the other, but the next question is can they support more than one logical interface? As in can a PCIe based M.2 SSD support AHCI *and* NVME?

I've been spending hours trawling the internet trying to figure this out, and found the below quote from Kingston Technology's website...

[B][I]"The M.2 spec was designed to accommodate both a SATA and PCIe interface  for SSDs. M.2 SATA SSDs will use the same controller currently on typical  2.5 in SATA SSDs. M.2 PCIe SSDs will use a controller specifically  designed to support the PCIe protocol. An M.2 SSD can only support one  protocol, but some systems have M.2 sockets that can support either SATA  or PCIe."

[/I][/B]What I find confusing is the last two sentences. Firstly, in the second to last sentence, the writer speaks of "*the" *PCIe protocol, which seems misleading to me as I believe that there are at least two protocols that can be used to control SSD's via PCIe - AHCI and the more recent NVMe?

Secondly, the final sentence seems to conflate protocols with buses, and the whole paragraph only seems to make *total* sense if you are laboring under the misapprehension that there is only one possible protocol (as far as controlling SSD's is concerned) that can be used for each different bus - one for SATA and another for PCIe

Should it be that the final sentence should actually read "*An M.2 SSD can only support one **bus**, but some systems have M.2 sockets that can support either SATA  or PCIe." *Which would then entertain the possibility that an M.2 PCIe based SSD may not be able to also support operation over a SATA bus, but it could support operation over PCIe via both AHCI and NVMe? 

> **CatKiller said:**
> Yes, that's what the SATAe standard was for. Rather than just doing "SATA, but faster," they got aligned with PCIe. So if an SSD maker had already designed their chip to use SATA, that will still work with the new standard. If they're going all in on PCIe, that will work, too. If a motherboard runs out of PCIe lanes, the SSD can still work over SATA. 

Yes I see what your saying (after looking up SATA express at least) and this does totally answer the question of if there are SSD's that can work over SATA and PCIe, but I was meaning specifically SSD's that use the M.2 form factor as opposed to connecting via a SATA express connector.

> I think it mostly happens at boot time, but yes, connections are made  based on which lanes are available. Hotplugging is supported by at least  some of these things.

Yes that makes the whole operation of the thing much, much clearer! Do you have any thoughts on what I wrote above in reply to Dennis N?

---

### Post by Dennis N on 2020-06-14
> As in can a PCIe based M.2 SSD support AHCI and NVME?

I don't think so. The controller chip (NVMe or SATA) is part of the drive hardware and the drive has one type of controller or the other. There is no dual mode controller that I know of.

Some old PCIe drives did use AHCI but you won't likely find such a drive offered today because no one would chose that over NVMe.

From a wikipedia article on M.2:

> At a high level, primary advantages of NVMe over AHCI relate to NVMe's ability to exploit parallelism in host hardware and software, based on its design advantages that include data transfers with fewer stages, greater depth of command queues, and more efficient interrupt processing.

---

### Post by TheFu on 2020-06-14
Be very careful when you read the motherboard data about m.2 storage connections.
Some will steal regular SATA ports when m.2 is used.  My Asus B450 loses SATA5 and SATA6 when m.2-1 gets used.
if you care about performance more than price, NVMe is the only option and prices have come down recently.

Be certain to pay attention to the bus slow speed and get an NVMe that can use that speed.  x2, x3, x4 matter greatly for NVMe slots.  Again, my Asus supports x4 with one m.2 NVMe, but only x2 when both are used.

Read the motherboard manual carefully. There will be a chart showing all these gotchas. Best to know them BEFORE purchase.

---

### Post by jcdenton1995 on 2020-06-14
> **Dennis N said:**
> Some old PCIe drives did use AHCI but you won't likely find such a drive offered today because no one would chose that over NVMe.

This is pretty much the impression I got from looking at what's available to buy, all current PCIe based drives, weather conventional PCIe cards or M.2, appear to use NVMe while the SATA based M.2 drives must still use AHCI (or something else I haven't seen but not NVMe obviously)

> There is no dual mode controller that I know of

I haven't seen anything myself, I'm just going based off articles that are floating around online that talk about "PCIe M.2 drives with support for NVMe" which I perhaps wrongly interpreted as meaning they were capable of another mode of operation, to which NVMe was an alternative that could be used if the system supported it - but I think what you say is correct, and what is actually meant is that said drives *only *support NVMe.

> **TheFu said:**
> Be very careful when you read the motherboard data about m.2 storage connections.
Some will steal regular SATA ports when m.2 is used.

Surely this is only the case for SATA based M.2 drives? as in the chipset only supports a limited number of SATA links, so using a SATA M.2 means some of the regular ports must be cut off?

> Be certain to pay attention to the bus slow speed and get an NVMe that can use that speed.

Is the "slow" speed the configuration that the drives will be run in when there aren't enough lanes available to run all drives using the max number of lanes they are capable of? like in your example of your ASUS supporting one M.2 in x4 but two drives must be run in x2?

---

### Post by oldfred on 2020-06-14
This has a good summary of questions on SATA & NVMe.
[https://superuser.com/questions/1535566/confusion-whats-the-difference-between-sata-nvme-m-2-and-pcie](https://superuser.com/questions/1535566/confusion-whats-the-difference-between-sata-nvme-m-2-and-pcie)
[https://www.pcpepper.com/sata-vs-msata-vs-ngff-m-2-vs-nvme-pcie-m-2-which-is-the-right-ssd-for-me/](https://www.pcpepper.com/sata-vs-msata-vs-ngff-m-2-vs-nvme-pcie-m-2-which-is-the-right-ssd-for-me/)

My 2014 build z97 has a M.2 connector. When I built system, I did not know or pay attention to it. But it is SATA only and uses ngff or next gen miniSATA but then not NVMe.

My 2016 build z170 then had M.2 for either SATA or NVMe, but back then NVMe drives were expensive, so I installed a SATA M.2 drive.

 I just upgraded to a new NVMe larger NVMe drive. Its quicker booting and loading large apps or files, but my normal use is not a lot faster. Most of my use is cached in RAM or is slowed down by the operator of the keyboard. 

I was going to move M.2 SATA to Z97 system, but needed to copy some data to Z170 and bought a M.2 SATA to USB adapter. Surprised  at how fast it is, I thought it was USB3 ports were part of why my flash drives were so slow, but SSD on USB3 as fast or faster than my SATA HDD. Have multiple large flash drives, so may now only buy SSDs for USB backup.

---

### Post by jcdenton1995 on 2020-06-14
Thanks, the first explanation in the first link you gave is particularly good.

What is still driving me up the wall is that many sources online refer to SATA and PCIe as "protocols", and while I'm aware that the term "bus" incorporates both the hardware and software in a data pathway, I'm sure that the actual protocols are AHCI and NVMe, are they not?

It's because of this that I find it confusing when I read about SATA vs NVMe, as is it not the case that SATA is the physical link and NVMe is a protocol used to communicate *over *a physical link, i.e PCIe. Although I appreciate that as NVMe can only be used over PCIe then it could be considered synonymous with it (as in SATA vs NVMe = SATA vs PCIe NVMe)

I hope that makes sense!

---

### Post by TheFu on 2020-06-15
I'm an engineer and happy to only know "enough" without knowing the details for everything.  The engineer in me is happy to know just enough information to solve the issue and move on.

And just to clarify - my Asus B450 SATA/NVMe restrictions don't apply to all Asus motherboards or even all B450 variants. Assume every motherboard is different, so pull the manual from the vendor and look through the installation guide for SSD m.2 storage. Carefully read the table and footnotes.  

I have exactly this: **ASUS ROG Strix B450-F Gaming Motherboard**
The manual is here: [https://www.asus.com/us/Motherboards/ROG-STRIX-B450-F-GAMING/HelpDesk_Manual/](https://www.asus.com/us/Motherboards/ROG-STRIX-B450-F-GAMING/HelpDesk_Manual/)
Direct English link: [https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/ROG_STRIX_B450_F_GAMING/E14401_ROG_STRIX_B450-F_GAMING_UM_WEB.pdf](https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/ROG_STRIX_B450_F_GAMING/E14401_ROG_STRIX_B450-F_GAMING_UM_WEB.pdf)
Page 22: has the table for m.2 SSDs support based on the GPU PCIe card uses.
Page 28: has the specifics for m.2 SSDs and SATA v NVMe options.> 
•       For AMD Ryzen[sup]TM[/sup] 2nd Generation / Ryzen[sup]TM[/sup] 1st Generation Processors:
	 - M.2_1 supports PCIE 3.0 x4 and SATA mode M Key design and type 2242 / 2260 / 2280 storage devices.
	 - M.2_2 supports PCIE 3.0 x4 M Key design and type 2242 / 2260 / 2280 / 22110 storage devices*.
•	 For AMD Ryzen[sup]TM[/sup] with Radeon[sup]TM[/sup] Vega Graphics Processors**
	 - M.2_1 supports PCIE 3.0 x4 and SATA mode M Key design and type 2242 / 2260 / 2280 storage devices.

	 * M.2_2 socket shares bandwidth with PCIE x16. When M.2_2 slot runs in PCIE mode, the PCIE x16_1 slot will run at x8 mode.
	 ** The M.2_2 socket is not supported for these CPU

Elsewhere in the manual (pg 9), 
> AMD Ryzen 2nd Generation / Ryzen 1st Generation Processors*
- M.2_1 socket 3 with M Key, Type 2242/2260/2280 (PCIE 3.0 x 4 and SATA modes) storage devices support**
- M.2_2 socket 3 with M Key, Type 2242/2260/2280/22110 (PCIE 3.0 x 4 mode) storage devices support***
- 2 x SATA 6Gb/s ports

**		When the M.2_1 Socket 3 is operating in SATA or PCIE mode, SATA6G_5/6 ports will be disabled.
***	 When the M.2_2 is occupied by M.2 device, PCIe x16_1 will run at x8 mode. 

Page 12:
> 1 x M.2_1 Socket 3 for M Key, type 2242/2260/2280 devices support, (supports PCIE and SATA modes)
1 x M.2_2 Socket 3 for M Key, type 2242/2260/2280/22110 devices support, (supports PCIE mode)


**Lots of caveats.**  Use both NVMe slots and the GPU becomes x8.  Use m2-1 as SATA and SATA port 5/6 are gone. If the CPU has onboard iGPU, then m2-2 cannot be used at all.  So, if I want 8 storage devices (6-SATA and 2-NVMe) then the GPU is only x8. I find that acceptable ... have added a 4-SATA controller to another PCIe slot to get a total of 12 HDDs supported as I retire older, less efficient, less capable systems.

Caveats. Know them BEFORE you buy stuff.

---

### Post by kurt18947 on 2020-06-15
> **oldfred said:**
> 
I was going to move M.2 SATA to Z97 system, but needed to copy some data to Z170 and bought a M.2 SATA to USB adapter. Surprised  at how fast it is, I thought it was USB3 ports were part of why my flash drives were so slow, but SSD on USB3 as fast or faster than my SATA HDD. Have multiple large flash drives, so may now only buy SSDs for USB backup.

Not all USB flash drives are created equal. I haven't really kept up with the latest and greatest but SanDisk made a family of USB 3 drives that used faster flash and SSD controllers. It was nearly as fast as SSDs at less $$$. More than $9.99 specials though as you'd expect.

To address JC's question, there are NVMe and SATA III SSDs. They are not interchangeable. I just recently installed my first MoBo with 2 M2 connectors, one NVMe and one SATA III. If I installed a SATA III M2 drive it would disable one of the plug-in SATA ports. I have an HP920 512 GB SSD which bench tested pretty well and it performs well but doesn't feel significantly faster than a mid-range SATA III SSD for typical desktop usage. If I were building a really compact system like the Intel NUC, M2 drives would shine because they're tiny. The physical size designators are something like 2280 or 22110. That means they're 22 mm wide and 80 or 110 mm long and a few mm thick. In other words, a little larger than a couple sticks of chewing gun.

---

### Post by jcdenton1995 on 2020-06-16
@TheFu Thanks that's really informative, and could definitely cause some headaches if someone was trying to figure out why a certain SSD wasn't being detected or something, if they weren't aware of those caveats! Also I guess if one was going to use the machine for gaming or something graphically intensive, but planned to add a NVMe SSD in M.2_2 then that could be a problem.

---

### Post by TheFu on 2020-06-16
> **jcdenton1995 said:**
> @TheFu Thanks that's really informative, and could definitely cause some headaches if someone was trying to figure out why a certain SSD wasn't being detected or something, if they weren't aware of those caveats!

Me writing 
>  Read the motherboard manual carefully. There will be a chart showing all these gotchas. Best to know them BEFORE purchase.  appears to not have been clear enough to get the point across like posting the actual, obtuse, words in the manual.  Too bad.

---

### Post by jcdenton1995 on 2020-06-16
> but doesn't feel significantly faster than a mid-range SATA III SSD

From just watching a few Youtube videos comparing loading times for vidja games between a HDD, SATA III SSD and NVMe SSD's, in practice the NVMe device improves on conventional SATA III loading times by one, maybe two seconds if your lucky over a fifteen to twenty second period.

I'm sure there are real benefits in other use cases like reading or writing large files, plus maybe this is actually caused by a bottleneck somewhere else?

---

### Post by jcdenton1995 on 2020-06-16
No I understood what you were saying before, what I meant is it's helpful to see how it is worded in the manual so I know what I'm looking at / for when I come to read other manuals for potential MB's I may buy.

>  the actual, obtuse, words in the manual

You are right they could have gone with just plain English.

---

### Post by TheFu on 2020-06-16
+1 on the fact that not all SSDs are equal.  That is a completely different consideration.  There are cheap brands, named-brands that resell other manufacturers's stuff and their are the higher quality brands across each market segment.

What I buy for putting together a computer to be resold is very different from what I buy for my own laptop, which is very different from what I buy for a VM server that will run 24/7 for 10 yrs.

Performance matters about 5th in my list of concerns.
[LIST]
[*]Size
[*]Price
[*]Endurance/durability as spec'd in TBW warranty
[*]Connection type
[*]Speed
[/LIST]

I won't buy any SSD that doesn't have published endurance numbers.  I've contacted some vendors who don't publish and they refused to provide those numbers. That tells me something about the quality of those devices just like a spinning HDD with a 90 day warranty says "this is crap".

To me, all SSDs are so much faster than spinning disks that it really doesn't matter anymore. OSes have been doing all sorts of tricks with spinning disks to make them "feel" faster.  Those same tricks don't help nearly as much for SSDs, except to reduce write cycles.  SSD endurance is all about write cycles per cell/sector.

There's lots of less-than-truthful marketing out there for storage.  WD has taken to calling some of their external storage "black" trying to play on the WD-Black 5 yr warranty HDDs for an external case that happens to be housed inside a black plastic case.  They've been calling some SSDs "black" too, when they only have 3 yr warranties and not the greatest TBW endurance numbers.  FWIW, a WD-Black HDD is a quality consumer disk with a warranty to match. The next step up gets into the professional/data center HDDs for 30% higher prices.  SSDs have a similar split.
[LIST]
[*]Cheap
[*]Consumer
[*]Pro
[*]Data Center
[/LIST]
The prices reflect the underlying technology used (usually).  The trick is to catch a sale on a low-end "pro" or high-end Consumer offer from a reputable SSD vendor.

The other trick is to monitor the TBW in the SMART data periodically, so you can predict when only 20% is left and plan a replacement. .... 
```
=== START OF INFORMATION SECTION ===
Device Model:     Micron_1100_MTFDDAV512TBN
...
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       10406
173 Unknown_Attribute       0x0032   098   098   000    Old_age   Always       -       41
174 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       35
202 Unknown_SSD_Attribute   0x0030   098   098   001    Old_age   Offline      -       2
246 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       13917089118
247 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       435623544
248 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       363193339
180 Unused_Rsvd_Blk_Cnt_Tot 0x0033   000   000   000    Pre-fail  Always       -       2480

```
Micron makes SSDs for other "name brands" you know, like Crucial.  The model above is a mid-range consumer that happened to be a deal for a few days. Micron has a PDF file which labels most attributes AND has a 1 page explanation for each.
173 - Average Block-Erase Count
174 - Unexpected Power Loss Count
202 - Percent Lifetime Remaining (by this value, 98% of the lifetime remains)
> This value gives the threshold inverted value of the data value below. That is, if 30% of
the lifetime has been used, this value will report 70%. A value of 0% indicates that 100%
of the expected lifetime has been used.
> Raw Data (48 bits)
This value is defined as:
 [insert complex formula; not really, this time]
Where:
E AVG = Average erase count for a super block (stripe of blocks)
B L = Erase count for which the part is rated (block life)

Attrib 246 isn't in the document, but I'd bet that is the TBW ... 13,917,089,118 ... about 13TB.  This is a TLC SSD and a little over 1 yr old.  The designed TBW limit is 240TB ... so, 240 / 13 = 18.5 yrs remaining. In theory, if the use patterns for it continue.  There is some specific high-write processing that I perform on spinning rust instead of this SSD to reduce the number of write cycles.  Seems to be working.   Also, never forget that the view the SSD provides to the OS of storage layout is 100% virtual and has nothing, ZERO, nada, to do with how cells are actually allocated into partitions or LVs or zpools.  What happens inside these modern SSDs as they try to write balance across all the cells equally hides all those details to the OS and humans.

Sorry for heading off topic so far.  Learn about TLC, SLC, MLC, QLC differences in SSDs to understand why QLC probably isn't the best choice unless only price matters.

---

### Post by Dennis N on 2020-06-16
_The common bottleneck_: NVMe paired with Sata SDDs (or even HDD) - data written/read from the SSDs is done at SATA speeds. This disappoints some people who think adding an NVMe drive makes everything faster.

I have that type of system (m.2 SATA + m.2 MVMe using PCIe adapter), but I knew this speed trap going in. But, since most of the work files I read and write are so small you don't notice lack of the NVMe speed.

Crucial is a brand of Micron. Micron Technology is an U.S. based company - Headquarters in Idaho!

---

### Post by kurt18947 on 2020-06-19
> **jcdenton1995 said:**
> From just watching a few Youtube videos comparing loading times for vidja games between a HDD, SATA III SSD and NVMe SSD's, in practice the NVMe device improves on conventional SATA III loading times by one, maybe two seconds if your lucky over a fifteen to twenty second period.

I'm sure there are real benefits in other use cases like reading or writing large files, plus maybe this is actually caused by a bottleneck somewhere else?

I think in data centers and the like is where NVMe really shines. I'm not in the business so my opinions are formed mostly by what i read.

---

