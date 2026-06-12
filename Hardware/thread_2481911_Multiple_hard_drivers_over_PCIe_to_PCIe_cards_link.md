---
title: "Multiple hard drivers over PCIe to PCIe cards linked?"
date: 2022-12-12
forum: Hardware
---

### Post by josephchrzempiec on 2022-12-12
Hello, I know this question that is not about normal hardware for ubuntu. I'm trying to figure out a way to run a Ubuntu server with 20 Hard drives in a second case nothing but hard drives somehow linked to the first server case with the motherboard. I don't have enough room to store 20 drives in my main case it can only handle 4 drives. Does anyone know of a reasonable cost way I can link my drive bay case to the server motherboard case that wouldn't break the bank as they say? 

Joseph

---

### Post by TheFu on 2022-12-13
It is called an external array.  

These devices exist already as either "DAS" Directly Attached Storage
or
"NAS" Network Attached Storage

For DAS, there are a few different connection methods. I use Infiniband and eSATA for my 2 arrays.  Infiniband is usually too expensive, but I got an adapter really cheap.  The drives themselves are either SAS or SATA.

For 20 drives, I'd lean towards making a NAS instead. then that NAS can provide NFS and iSCSI over the network.  Heck, you can also use AoE (ATA over Ethernet) which has lower overhead than iSCSI.  Linux has supported iSCSI for 20+ yrs.

If you are stuck with the DAS choice, you'll likely want to use a quality SAS controller with 4-SAS ports.  Each SAS port can connect to 4 SATA drives using a cable.  Look for an LSI HBA (LSI is the brand, HBA = Host Bus Adapter; a fancy name for drive controller).

Addonics used to make external array hardware for relatively little cost compared to everyone else.  Their product offers seem to be just a tiny amount of what they had 10 yrs ago, unfortunately. They used to sell cases, converters, connectors, for lots and lots of different storage needs.

I have a little 4-drive hot-swap cage that fits into a 3x5.25in area that most mid and full towers have. Roswell made this plastic thing for $45 for a few years. The caddies hold the drives and they "click" into the rear SATA/power slots which have internal SATA connectors for a motherboard or internal PCIe SATA controller. The Rowsell drive cage has a huge fan that pulls air over the drives to keep them cool.  Had to replace that fan after a few years - got a Noctua 120 silent and never looked back.  Others make a 5-drive in 4x5.25in drive cage too.

What you think won't break the bank is subjective and meaningless without a budget.  For many people, swapping 10TB disks for 18TB disks is more cost effective than having lots of drives due to the cost of drive controllers, power, fancy connectors, and external arrays.  I'm running into that issue now.  I have (3) 4-drive arrays of different drive sizes.  One has 2TB disks, another has 4TB disks and the last has 8TB disks.  Replacing the 4x2TB with 16TB would be a massive storage upgrade just by swapping HDDs.  The real issue is whether all the connecting hardware will support drives of those sizes or not and because Infiniband is just a cable in my situation, that means the SATA controller inside the computer will need to support HDDs of that size too.

If you have (20) 16TB drives, that is thousands in just the HDDs already, so spending thousands on disk controllers is more reasonable.  Be certain to verify that the LSI board chips are supported in the Linux kernel, not by external drivers.  Don't get burned with hardware that doesn't actually work.

So you have some reading to be done to make informed choices.

---

### Post by josephchrzempiec on 2022-12-15
Hello Fu, Thank you for the reply back. I'm pretty much open to anything. I have even tried anything yet. I'm still in the figuring out how to connect two boxes together. oe being the server and the second box the hard drives box. I'm trying to build it as a nas system. Each hard drive is 2TB drives nothing on them all brandnew. I got them when they was on sale and store thm into the right time to build something.

---

### Post by TheFu on 2022-12-15
> **josephchrzempiec said:**
> Hello Fu, Thank you for the reply back. I'm pretty much open to anything. I have even tried anything yet. I'm still in the figuring out how to connect two boxes together. oe being the server and the second box the hard drives box. I'm trying to build it as a nas system. Each hard drive is 2TB drives nothing on them all brandnew. I got them when they was on sale and store thm into the right time to build something.

NAS - NETWORK!  That means you need to have a little computer in the same box and 1+ network adapters which are how the other computers access the storage.  

That isn't what the subject says.  The subject doesn't want to use a network. It wants DAS - Directly Attached Storage.

These are very different things.
There are tiny computers that just provide NAS capabilities. Addonics used to sell them for about $100. [https://www.amazon.com/Addonics-NAS-4-0-Adapter-NAS40ESU/dp/B0093I4KRO/](https://www.amazon.com/Addonics-NAS-4-0-Adapter-NAS40ESU/dp/B0093I4KRO/)  They couldn't do anything else. No virtual machines. No Docker containers, just NAS. Usually NFS or iSCSI.  NFS can be accessed by multiple client devices concurrently.  iSCI is a block device protocol and implies only 1 client having access at a time.  Both appear like local storage to the client systems, but iSCSI is lower-level and better for things like holding a DBMS.

The trade off between the different NAS options are performance, price, flexibility.  Usually only 1 can be picked.  Avoid USB anywhere in the storage connections. Use SATA, eSATA, or SAS only.  Some routers allow connecting USB storage. Don't do that, especially if the router is your WAN router. Router vendors have proven multiple times they can't get the security correct for storage. Seems most make everything available to the world, not just your LAN with hardly any hacking required.  One vendor had their own servers hacked that provided access to routers+storage for all their clients. Beware.

Sadly, the raspberry pi like systems are all poor performers, so should be avoided.  Raspberry Pis are great little machines, but they aren't cheap for what you get and they aren't designed to move lots of data, sadly.  That's what a NAS needs.  Probably best to stick with x86-64 systems.  I'd look for low-end Ryzens, which can be had for under $100 now. Add a cheap microATX MB and RAM and for about $200 total, you can reuse old stuff and have a decent, flexible, NAS.  [https://pcpartpicker.com/list/P6Cf3b](https://pcpartpicker.com/list/P6Cf3b) is a quick PC Part Picker Build for just 3 things. $203.  I find their prices to be a bit higher than what is really available. Often, I can find a MB+CPU combo deal for $20 off.  Went with 1x8G of RAM to get started.  As a NAS, I've seldom needed more than 4G RAM.  Mine running all those VMs is using just 5.2G of RAM now. Most of the RAM is being used as a buffer, which is nice, but hardly needed 99.999% of the time.  To be clear, I'm not suggesting those 3 parts.  The Ryzen 3200G is not the best value right now, even if it is the cheapest with iGPU.  The 5600G for $110 is the best value and massively faster for less than $20 more.

2TB drives really aren't worth putting into arrays anymore, I'm sad to say.  I've seen 8TB new for the price of 2x2TB just last week.  The cost per port TB is the problem.  8TB drives are 4x better than 2TB on a per-port-cost basis.  I'm retiring 2TB drives now, like I retired 320GB drives 12 yrs ago. It is necessary to gain access to the ports.

When very few people do something, there is usually a reason they don't.  Building an external disk array to be directly connected to 1 other system just isn't done for many reasons.  Building a NAS is something I've done a few times.  My home-built NAS boxes are much more capable for much less money than the reputable branded NAS devices.  Just ensure you start with a base computer that can do more.  My current NAS has a Ryzen 5600G, 16G of RAM and about 40TB connected.  It runs many virtual machines, JellyFin, Calibre, NextCloud, Wallabag, and a few others easily.  It also handles transcoding of recorded TV at about 6x.  $1000 NAS boxes don't do all that.  Cost me a little over $400 to build last year. I reused parts, just the CPU, MB, and RAM are new.  I did add a new 8TB WD-Black 3.5in HDD a few weeks ago to the primary storage.  Effectively, that's 4TB more, since I backup everything.  I chunk my storage as 4TB allocations (really 3.6TB after formatting) on that system, so I had to move some stuff around which took over a day to run (about 5 min of my time).

Anyway, some more things to consider.

---

