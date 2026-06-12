---
title: "Seeking advice on selecting motherboard"
date: 2022-01-14
forum: Hardware
---

### Post by satimis on 2022-01-14
Hi all,

I'm prepared to build a new PC, no gaming, with following configuration;

CPU - AMD Ryzen 7 5800X
Graphic card - I have a MSI GeForce GTX 1650 graphic card resting on shelves.

MSI GeForce GTX 1650 Super Gaming X Dual Fan Graphics Card - 4 GB
[https://www.memoryc.com/31006-msi-geforce-gtx-1650-super-gaming-x-dual-fan-graphics-card-4-gb.html](https://www.memoryc.com/31006-msi-geforce-gtx-1650-super-gaming-x-dual-fan-graphics-card-4-gb.html)

RAM - DDR4/DDR5 32G/64G

HDD - 1TB NVMe PCIe Gen4x4 SSD for running OS and other software

Virtualization - Oracle VirtualBox

HDD - 4TB WD, already available, for data storage only, without OS installed.

Please recommend an ASUS motherboard ?
Shall I go DDR4 or DDR5 ?
Do I need 64G RAM or 32G will be suitable for my use ?

Please advise.  Thanks in advance.

(Remark: The reason to indicate ASUS brand is;
I have been using ASUS motherboard for long time.
It never failed letting me disappointed.

Other brand also will be considered)

Regards

---

### Post by him610 on 2022-01-14
If you want a [Asus | MSI | Gigabyte | Etc ] mother board, go to the manufacturer's website, read and compare the specs, and the recommended memory will be listed. It's part of system engineering. You can also go to pcpartspicker, and they will match different components and assemblies up for you.

That being said...( these parts should play together nicely)
        AMD Ryzen 7 5800X 3.8 GHz 8-Core Processor
	Cooler Master MASTERLIQUID ML240L RGB V2 65.59 CFM Liquid CPU Cooler
	Asus TUF GAMING X570-PLUS (WI-FI) ATX AM4 Motherboard
	G.Skill Ripjaws V Series 32 GB (2 x 16 GB) DDR4-3200 CL16 Memory
	Cooler Master V SFX Gold 850 W 80+ Gold Certified Fully Modular SFX Power Supply

---

### Post by Frogs Hair on 2022-01-14
Unless you are building a video intensive graphics work-station you shouldn't need 64 Gb of memory. 32 is recommended for heavy multitasking in work environment and 16 for average use. Unless you are trying to future-proof the computer don't spend the money.The CPU also needs to be capable of making use of the memory installed.

---

### Post by satimis on 2022-01-14
> **Frogs Hair said:**
> Unless you are building a video intensive graphics work-station you shouldn't need 64 Gb of memory. 32 is recommended for heavy multitasking in work environment and 16 for average use. Unless you are trying to future-proof the computer don't spend the money.The CPU also needs to be capable of making use of the memory installed.
Thanks for your advice.

I'm running VirtualBox here with 4 VMs running 40 cloned websites.  The cloned websites are not all running at the same time.  They serve as the backup sites of the live websites running on Internet.  Should there is any problem on the live websites I just clone the local website to replace the problematic live website.  Periodically I'll run the local cloned websites to upgrade their software.

Should I pick DDR5 or DDR4 RAM ?

Regards

---

### Post by satimis on 2022-01-14
> **him610 said:**
> If you want a [Asus | MSI | Gigabyte | Etc ] mother board, go to the manufacturer's website, read and compare the specs, and the recommended memory will be listed. It's part of system engineering. You can also go to pcpartspicker, and they will match different components and assemblies up for you.
Thanks for your advice.

Whether following website ?
[https://pcpartpicker.com/](https://pcpartpicker.com/)
[https://pcpartpicker.com/forums/](https://pcpartpicker.com/forums/)

> 
....
	Asus TUF GAMING X570-PLUS (WI-FI) ATX AM4 Motherboard
....
        Cooler Master V SFX Gold 850 W 80+ Gold Certified Fully Modular SFX Power Supply
TUF GAMING X570-PLUS (WI-FI)
[https://www.asus.com/Motherboards-Components/Motherboards/TUF-Gaming/TUF-GAMING-X570-PLUS-WI-FI/](https://www.asus.com/Motherboards-Components/Motherboards/TUF-Gaming/TUF-GAMING-X570-PLUS-WI-FI/)

Sorry I forgot to mention that I already have a brand-new power supply available:
Corsair CX550M 550 Watt
[https://www.corsair.com/us/en/Categories/Products/Power-Supply-Units/cxm-series-2015-config/p/CP-9020102-NA](https://www.corsair.com/us/en/Categories/Products/Power-Supply-Units/cxm-series-2015-config/p/CP-9020102-NA)

Regards

---

### Post by Yellow Pasque on 2022-01-18
> Shall I go DDR4 or DDR5 ?

You don't have a choice. Socket AM4 doesn't support DDR5.

---

### Post by TheFu on 2022-01-18
I have a Ryzen 5600G.  Ryzens are picky about RAM, so be certain to pick the RAM from the exact list provided by the motherboard vendor's list.  I didn't and have some RAM that won't run at the rated speed.  3200 doesn't work.  I'm running at 2666Mhz on that system.  On another Ryzen, using supported RAM, 3200 Mhz works great.

Also, beware that new Asus motherboards have different NIC options.  Some of those NICs had issues with Ubuntu to the point where people ended up buying a $30 Intel NIC to install rather than fight with the drivers.  I specifically bought an older B450 to get an Intel I211 NIC that is well supported. The newer Intel 2.5Gbps NIC in the B550 MB has threads here with the issues. Beware.  I also avoid Realtek NICs.  Been burned too many times with issues and failures.

I'm using 16G RAM in one of my systems and 32G in the other. Can't say that most people would really need lots of RAM unless they are doing 4-8K video editing. My laptop (Core i5 8th gen) has 8G of RAM and it is 100% great too.  I just manage my expectations for what processing it does and run fewer VMs and only do very light video editing on it.

I avoid the newest RAM for as long as possible.  If I had a choice, my Ryzens would be using DDR3 RAM - which I had laying around rather than forced obsolescence that is the "faster" RAM junk.  For anything I'm doing, faster RAM is barely noticeable and I'd rather reuse old RAM saving $100.

---

### Post by satimis on 2022-01-18
Hi all,

Lot of thanks for your advice.

**The [COLOR="#FF0000"]preliminary configuration[/COLOR] of my new PC is as follow** :

**CPU:**
AMD Ryzen 7 5800X 100-100000063WOF 8C/16T,3.8GHz,36MB Cache,TSMC 7nm,Socket AM4 CPU w/o Fan	

**Motherboard:**
ASUS ROG STRIX B550-F GAMING WIFI II AM4 Socket,Intel 2.5Gb Lan,WiFi 6E,USB3.2 Gen2 ATX M/B
[https://rog.asus.com/motherboards/rog-strix/rog-strix-b550-f-gaming-wi-fi-model/](https://rog.asus.com/motherboards/rog-strix/rog-strix-b550-f-gaming-wi-fi-model/)

**RAM:**
ADATA 32GB Premier AD4S320032G22-SGN DDR-4 3200MHz (1x32GB) SODIMM

**HDD**
**[COLOR="#FF0000"]1)[/COLOR]**
SSD - running Ubuntu 20.04 and VirtualBox
ADATA 2TB XPG GAMMIX S70 BLADE AGAMMIXS70B-2T-CS M.2 2280 PCIe Gen4x4 NVMe SSD

**[COLOR="#FFA07A"]2)[/COLOR]**
SSD - running Windows 10 for editing old video and old photos
ADATA 1TB XPG GAMMIX S70 BLADE AGAMMIXS70B-1T-CS M.2 2280 PCIe Gen4x4 NVMe SSD
**(Dual boot controlled via BIOS)**

**Graphic card** - already available
MSI GeForce GTX 1650 Super Gaming X Dual Fan Graphics Card - 4 GB
[https://www.memoryc.com/31006-msi-geforce-gtx-1650-super-gaming-x-dual-fan-graphics-card-4-gb.html](https://www.memoryc.com/31006-msi-geforce-gtx-1650-super-gaming-x-dual-fan-graphics-card-4-gb.html)

**Power Supply:**
Corsair CX550M 550 Watt - already available, brand-new still packed in box
[https://www.corsair.com/us/en/Categories/Products/Power-Supply-Units/cxm-series-2015-config/p/CP-9020102-NA](https://www.corsair.com/us/en/Categories/Products/Power-Supply-Units/cxm-series-2015-config/p/CP-9020102-NA)

This config is NOT final yet.  At present I'm still busy in setting up files transfer;
1) Btw Linux/Win 10 guests and Ubuntu 20.04 host on KVM/QEMU
2) Btw Linux drive and Win 10 drive in the same PC
(There are many solutions suggested.  I expect finding a way suitable for my use.  

I'll do graphic editing on 4K display and sooner on 8K display when its price dropped)

**Comment on the preliminary config of my new PC is welcome.**

Remark: I won't run this PC 24/7 as server

Regards

---

### Post by TheFu on 2022-01-19
That's the motherboard I specifically avoided due to problems with the NIC driver. Has that been solved yet?
I don't know the power draw for the nVidia card, but seems most people get 800W PSUs for a card like that.

---

### Post by satimis on 2022-01-19
> **TheFu said:**
> That's the motherboard I specifically avoided due to problems with the NIC driver. Has that been solved yet?

OK, I'll go back to my previous pick;

TUF GAMING X570-PLUS 
[https://www.asus.com/Motherboards-Components/Motherboards/TUF-Gaming/TUF-GAMING-X570-PLUS/](https://www.asus.com/Motherboards-Components/Motherboards/TUF-Gaming/TUF-GAMING-X570-PLUS/)

It seems to me that there is only one Port for PCIe Gen4x4 NVMe SSD on this motherboard ?

I needs 2 Ports for;
2TB PCIe Gen4x4 NVMe SSD
and
1TB PCIe Gen4x4 NVMe SSD

> 
I don't know the power draw for the nVidia card, but seems most people get 800W PSUs for a card like that.
No problem if my Corsair CX550M 550 Watt PSU doesn't work, I just purchase a new 800W PSU

Regards

---

### Post by Yellow Pasque on 2022-01-19
> RAM: ADATA 32GB Premier AD4S320032G22-SGN DDR-4 3200MHz (1x32GB) SODIMM

Try again. That's a laptop RAM stick (SODIMM). What you want is a 32GB kit (2 x 16GB).


> **TheFu said:**
> I don't know the power draw for the nVidia card, but seems most people get 800W PSUs for a card like that.

The graphics card is only going to pull 100W max. Nvidia recommends a 350W PSU. Where did you come up with 800W?!!

---

### Post by KBar on 2022-01-19
Two things:
[LIST=1]
[*]Always go for dual-channel memory. Instead of buying a single 32 GB memory chip, split it into 2x16 or 4x8. 
[*]If possible, avoid Nvidia cards. 
[/LIST]

---

### Post by QIII on 2022-01-19
> If possible, avoid Nvidia cards. 

There are those who would say to avoid AMD cards.  Do diligent research and purchase a card that fulfills the needs of the intended use, no matter the OEM.


> Always go for dual-channel memory. Instead of buying a single 32 GB memory chip, split it into 2x16 or 4x8. 

There is a good deal of conflicting research on the performance gains from single to double to quad (assuming the mobo/CPU allows quad -- Threadrippers and I9s and such) and splitting it out into smaller chunks.  

In many use cases for most users, the improvement is inconsequential to modest at best.  In other applications, like heavy CPU number crunching with the need to feed rapid CPU L3 cache unloading/re-loading, the performance improvement can be very significant.  It may approach 2x or 4x the performance asymptotically, but it will never really get there.  

Virtual machines make dual or quad channel memory -- in high quantity if you want to run a lot of them at once -- desirable as well.

In any case, yes.  Since dual-channel memory is available and not significantly more expensive, go with that.  And, while you're at it, halve or quarter the total into smaller modules.  That is often less expensive.  Plus, going that route may be future-proofing against some new killer app that will come out next week where it will be helpful.

With regard to PSUs, recommendations are made by OEMs without any idea (how can they have one?) what other loads are put on the machine by other hardware. 

My philosopy is:  Don't cheap out on the PSU.  A PSU failure can wreck everything else.  Go with a top-flight OEM and a top-flight model.  There is a reasonable limit, of course, but a PSU rated at higher wattage is better at dissipating the heat when stressed at half its rated wattage than a PSU barely able to keep up.  Bigger heat sinks, bigger fans, etc.  Heat, being the killer of electronics that it is, is our enemy.  For a given load, a PSU with excess power to spare will last longer -- but that doesn't mean one should get a 1500W PSU for a machine that is expected to to require 400W total.

---

### Post by satimis on 2022-01-19
> **Yellow Pasque said:**
> Try again. That's a laptop RAM stick (SODIMM). What you want is a 32GB kit (2 x 16GB).
Thanks for your advice.

I'll pick;
ADATA 32GB Kit AX4U360016G18I-DT60 XPG SPECTRIX D60G DDR4 3600MHz (2x16GB) RGB LED

I thought that the motherboard can take 128G RAM.  If starting with a 32G module, later if needed, I can increase 32G -> 64G -> 128G

Now I have to start with;
Corsair 64GB Kit CMK64GX4M2D3600C18 Vengeance LPX DDR4 3600MHz (2x32GB) 

if I need 128G RAM later.

Regards

---

### Post by satimis on 2022-01-19
> **KBar said:**
> Two things:
[LIST=1]
[*]Always go for dual-channel memory. Instead of buying a single 32 GB memory chip, split it into 2x16 or 4x8. 
[*]If possible, avoid Nvidia cards. 
[/LIST]
Your advice noted and thanks

Regards

---

### Post by Yellow Pasque on 2022-01-19
Frankly, I think your best bet is a 64GB kit (4 x 16) instead of trying to deal with 32GB sticks. Just because 128GB of RAM in a desktop mobo is theoretically possible, it doesn't mean it's a good idea. If you've really got visions of 128GB of RAM, start looking at Threadrypper CPU's/mobos.
I suggest you stick to the QVL and decide if you want 32GB or 64GB from the get go. These days, you're best off buying your RAM as a kit instead of trying to mix and match and add more later.
[https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/PRIME_X570-PRO/Memory_QVL_for_AMD_Ryzen_5000_Series_Processors_X570_0423.pdf](https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/PRIME_X570-PRO/Memory_QVL_for_AMD_Ryzen_5000_Series_Processors_X570_0423.pdf)

---

### Post by satimis on 2022-01-19
> **Yellow Pasque said:**
> Frankly, I think your best bet is a 64GB kit (4 x 16) instead of trying to deal with 32GB sticks. Just because 128GB of RAM in a desktop mobo is theoretically possible, it doesn't mean it's a good idea. If you've really got visions of 128GB of RAM, start looking at Threadrypper CPU's/mobos.
I suggest you stick to the QVL and decide if you want 32GB or 64GB from the get go. These days, you're best off buying your RAM as a kit instead of trying to mix and match and add more later.
[https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/PRIME_X570-PRO/Memory_QVL_for_AMD_Ryzen_5000_Series_Processors_X570_0423.pdf](https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/PRIME_X570-PRO/Memory_QVL_for_AMD_Ryzen_5000_Series_Processors_X570_0423.pdf)
Good suggestion.

I'll pick;
Corsair 64GB Kit CMW64GX4M4D3600C18 Vengeance RGB PRO DDR4 3600MHz (4x16GB)

I have 3 desktop PCs
2 of them - 32G RAM
1 - 8G (it will retire)

Regards

---

### Post by TheFu on 2022-01-19
I wouldn't touch Realtek L8200A.  I'm not a Realtek fan.

> The graphics card is only going to pull 100W max. Nvidia recommends a 350W PSU. Where did you come up with 800W?!! 
I don't do high end GPUs - so always assumed they took 300W based on LTT comment a few days ago.  Of course, he was building a gaming rig with a 3080.  60 --> 80 are they really that different?  IDK.

> No problem if my Corsair CX550M 550 Watt PSU doesn't work, I just purchase a new 800W PSU

I was going to post that being prepared to get a new PSU was a good idea, if it was necessary, but that under powered PSUs often have odd symptoms that aren't easily traced. Sometimes everything works great.  Until it doesn't.  I've had a GPU go bad (likely old age) and it never appeared to be failing, just the OS became unstable.  Replacing the GPU and nothing else fixed all the stability issues on that machine.

As for AData - I've not had any issues with them ever, but when it comes to SSDs, I've learned to buy Samsung and only Samsung.  I have been dissatisfied with some low-end SSDs, but that was 5+ yrs ago.  Perhaps these days all that is done?

> If possible, avoid Nvidia cards. 
I've been buying nVidia GPUs for 20 yrs and they have become a pain on Linux the last 5 yrs.  I've had good luck with iGPUs from AMD and Intel, assuming the performance provided meets your needs.  I had to move to a bleeding edge kernel with my 5600G to get iGPU support before I am willing to migrated to a new OS which has the needed kernel in the HWE line.
It is generally accepted that nVidia GPUs are faster than AMD, but if you aren't at the highest end devices ($1200+), then I'd probably just buy the performance needed in an AMD GPU.

However, the OP is reusing an existing nvidia GPU, so I'm 100% behind that choice. The 1650 is still a great card with lots of life left.

x4 vs x3 ... does that truly matter in your workload?  I prefer to wait until something isn't the hottest new thing before buying to save a few $$$. Not sure you'll see my spend over $100 for any SSD. I'm more likely to get HDDs and use part of an SSD for ZFS cache purposes to hide the performance that HDDs have.  [https://en.wikipedia.org/wiki/ZFS#Caching_mechanisms:_ARC,_L2ARC,_Transaction_groups,_ZIL,_SLOG,_Special_VDEV](https://en.wikipedia.org/wiki/ZFS#Caching_mechanisms:_ARC,_L2ARC,_Transaction_groups,_ZIL,_SLOG,_Special_VDEV)

Good point on using as many RAM slots as possible.  Plus, in 2 more years, 32G sticks should be cheap. I'm all about buying what I need today, not what I might need in 3 yrs.

---

### Post by TheFu on 2022-01-19
[https://ubuntuforums.org/showthread.php?t=2471005&p=14076397#post14076397](https://ubuntuforums.org/showthread.php?t=2471005&p=14076397#post14076397) has an interesting thing related to SSD performance. Worth researching BEFORE buying.

---

### Post by TheFu on 2022-01-20
[https://www.reddit.com/r/ASUS/comments/kppyoi/psa_asus_motherboards_with_intel_i225v_25gb_nic/](https://www.reddit.com/r/ASUS/comments/kppyoi/psa_asus_motherboards_with_intel_i225v_25gb_nic/) has specific Asus MBs and NICs that are of concern, so it you can avoid the problem MB lots and get a known good Intel 2.5Gbps NIC, fantastic.
ROG Strix X570-[COLOR="#FF0000"]E[/COLOR] Gaming is fine. Prior versions, not so much.
Looks like all the ROG Strix B550 versions are bad for Windows AND Linux.  

Intel and Asus are claiming there aren't any issues and ignoring it.

---

### Post by satimis on 2022-01-20
> **TheFu said:**
> [https://www.reddit.com/r/ASUS/comments/kppyoi/psa_asus_motherboards_with_intel_i225v_25gb_nic/](https://www.reddit.com/r/ASUS/comments/kppyoi/psa_asus_motherboards_with_intel_i225v_25gb_nic/) has specific Asus MBs and NICs that are of concern, so it you can avoid the problem MB lots and get a known good Intel 2.5Gbps NIC, fantastic.
ROG Strix X570-[COLOR="#FF0000"]E[/COLOR] Gaming is fine. Prior versions, not so much.
Looks like all the ROG Strix B550 versions are bad for Windows AND Linux.  

Intel and Asus are claiming there aren't any issues and ignoring it.
Thanks for your advice.

How about
ASUS AM4 TUF GAMING X570-PLUS
[https://www.asus.com/Motherboards-Components/Motherboards/TUF-Gaming/TUF-GAMING-X570-PLUS/techspec/](https://www.asus.com/Motherboards-Components/Motherboards/TUF-Gaming/TUF-GAMING-X570-PLUS/techspec/)

I don't need WIFI but I need 2 ports for;

2 (two) NVMe PCIe 4.0x4 cards

---

### Post by him610 on 2022-01-21
> ...I need 2 ports for; 2 (two) NVMe PCIe 4.0x4 cards
That makes it a requirement.

You need to look for that in the motherboard specs.

---

### Post by satimis on 2022-01-21
> **him610 said:**
> That makes it a requirement.

You need to look for that in the motherboard specs.
According to:

8 Best Motherboards for Ryzen 7 5800X Reviews in 2022
[https://www.electronicshub.org/best-motherboards-for-ryzen-7-5800x/](https://www.electronicshub.org/best-motherboards-for-ryzen-7-5800x/)
MSI MPG X570 Motherboard
ASUS AM4 TUF Gaming X570-Plus
......

1)
MSI MPG X570 GAMING PLUS 
[https://www.msi.com/Motherboard/MPG-X570-Gaming-PLUS/Specification](https://www.msi.com/Motherboard/MPG-X570-Gaming-PLUS/Specification)
```

Storage
AMD® X570 Chipset
    4x SATA 6Gb/s ports(SATA3-SATA6)
    2x M.2 slots (Key M)  *******
        M2_1 slot(from AMD® Processor)
        - Supports PCIe 4.0 x4 (3rd Gen AMD Ryzen&#8482;)
        - Supports PCIe 3.0 x4 (2nd Gen AMD Ryzen&#8482;/ Ryzen&#8482; 4000 G-Series, Ryzen&#8482; with Radeon&#8482; Vega Graphics and 2nd Gen AMD Ryzen&#8482; with Radeon&#8482; Graphics)
        - Supports 2242/ 2260/ 2280/ 22110 storage devices
        M2_2 slot (from AMD® X570 Chipset)
        - Supports PCIe 3.0 x4 (2nd Gen AMD Ryzen&#8482;/ Ryzen&#8482; 4000 G-Series,Ryzen&#8482; with Radeon&#8482; Vega Graphics and 2nd 
....

```
2x M.2 slots for "PCIE 4.0 x4 "


2)
ASUS TUF GAMING X570-PLUS
[https://www.asus.com/Motherboards-Components/Motherboards/TUF-Gaming/TUF-GAMING-X570-PLUS/techspec/](https://www.asus.com/Motherboards-Components/Motherboards/TUF-Gaming/TUF-GAMING-X570-PLUS/techspec/)

-> Details
```

Storage
AMD Ryzen&#8482; 5000 Series/ 3000 Series Desktop Processors :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support
AMD Ryzen&#8482; 5000 G-Series/ 4000 G-Series/ 3000 G-Series/ 2000 Series/ 2000 G-Series Desktop Processors :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 3.0 x4 and SATA modes) storage devices support
AMD X570 chipset :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support
8 x SATA 6Gb/s port(s)
Support Raid 0, 1, 10

```
It seems to me, there are "2 x M.2 Socket 3" for "PCIE 4.0 x4 and SATA modes" ?

Both motherboards seems suitable for me?  I don't need WIFI.

Please comment.  Thanks

Regards

---

### Post by him610 on 2022-01-21
```

Storage
AMD Ryzen™ 5000 Series/ 3000 Series Desktop Processors :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support
AMD Ryzen™ 5000 G-Series/ 4000 G-Series/ 3000 G-Series/ 2000 Series/ 2000 G-Series Desktop Processors :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 3.0 x4 and SATA modes) storage devices support
AMD X570 chipset :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support
8 x SATA 6Gb/s port(s)
Support Raid 0, 1, 10

```
This entry ...
```

AMD Ryzen™ 5000 Series/ 3000 Series Desktop Processors :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support

```
is different from this entry...
```

AMD Ryzen™ 5000 G-Series/ 4000 G-Series/ 3000 G-Series/ 2000 Series/ 2000 G-Series Desktop Processors :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 3.0 x4 and SATA modes) storage devices support

```
is different from this entry...
```

AMD X570 chipset :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support

```
It is kind of confusing for Asus to write it like that. You might want to look at how another manufacturer specifies a similar motherboard.

---

### Post by satimis on 2022-01-21
> **him610 said:**
> ```

Storage
AMD Ryzen™ 5000 Series/ 3000 Series Desktop Processors :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support
AMD Ryzen™ 5000 G-Series/ 4000 G-Series/ 3000 G-Series/ 2000 Series/ 2000 G-Series Desktop Processors :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 3.0 x4 and SATA modes) storage devices support
AMD X570 chipset :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support
8 x SATA 6Gb/s port(s)
Support Raid 0, 1, 10

```
This entry ...
```

AMD Ryzen™ 5000 Series/ 3000 Series Desktop Processors :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support

```
is different from this entry...
```

AMD Ryzen™ 5000 G-Series/ 4000 G-Series/ 3000 G-Series/ 2000 Series/ 2000 G-Series Desktop Processors :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 3.0 x4 and SATA modes) storage devices support

```
is different from this entry...
```

AMD X570 chipset :
1 x M.2 Socket 3, with M Key, Type 2242/2260/2280/22110(PCIE 4.0 x4 and SATA modes) storage devices support

```
It is kind of confusing for Asus to write it like that. You might want to look at how another manufacturer specifies a similar motherboard.
Yes, you're right.  I'm also very confused.

The spec of "MSI MPG X570 GAMING PLUS" is quite clear;```

Storage
AMD® X570 Chipset
    4x SATA 6Gb/s ports(SATA3-SATA6)
    2x M.2 slots (Key M)  *******
        M2_1 slot(from AMD® Processor)
        - Supports PCIe 4.0 x4 (3rd Gen AMD Ryzen™)
        - Supports PCIe 3.0 x4 (2nd Gen AMD Ryzen™/ Ryzen™ 4000 G-Series, Ryzen™ with Radeon™ Vega Graphics and 2nd 
...

```
If I can't find an ASUS motherboard suitable for my requirement, I may select this motherboard but it has been on market sometimes.

There is no urgency.  I'm now full engaged on setting up folders sharing between Linux/Windows guest and Ubuntu host of KVM/QEMU and to install Video Edting Software on Windows 10.

Regards

---

### Post by aug7744 on 2022-01-25
If have computer component that work long life without issues better for one user and not for other user is mainboard and hard disk.
Have user no luck using Asus and good luck using Seagate disks. Other user have luck using Gigabyte and WD.

---

### Post by satimis on 2022-01-25
> **aug7744 said:**
> If have computer component that work long life without issues better for one user and not for other user is mainboard and hard disk.
Have user no luck using Asus and good luck using Seagate disks. Other user have luck using Gigabyte and WD.
I have built my own PC since more than 15 years ago.  All times I used AMD/Intel CPU + Asus motherboard.  Only once I used Intel CPU + Gigabyte motherboard and finally I have to change the motherboard from its agent.

I have PCs here running AMD CPU + Asus motherboard for more than 10 years, still working great without problem.  My daily working PC is running AMD Ryzen 5 CPU + Asus motherboard, built about 4 years ago.

I'm prepared to build a new PC running AMD Ryzen 7 CPU + Asus motherboard with 64G ram.  The motherboard must provide 2 NVMe PCIe Gen 4.0x4 ports/slots.

The PC is not for gaming nor running 24/7

That is what I'm now searching.

Regards

---

