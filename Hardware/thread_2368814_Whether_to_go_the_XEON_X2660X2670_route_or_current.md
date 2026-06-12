---
title: "Whether to go the XEON X2660/X2670 route or current Intel desktop processor route"
date: 2017-08-15
forum: Hardware
---

### Post by agh98 on 2017-08-15
Hi all,
My first post here and, while I'm not new to linux, I am new to ubuntu and the forums. My goal is to spend around $500-600 and create a server for my small business to serve up a web application with python/django/etc. (low bandwidth, really a back-end tool for a couple of users), a mysql database, a git server and other misc odds and ends. I want it to run headless and - while I know little about modern virtualization - I imagine I will want to separate the major applications via virtual instances or containers. I have much to learn about LXD, xen, etc. I do want to separate the database from the outward facing web component, however.

This post is less about software than hardware, however. I am intrigued by the possibility of using older 2660/2670 xeon processors on a server motherboard (with ECC ram which I imagine is a plus for the database) but am having a hard time coming up with clear cost/benefit analyses of this approach versus a mother desktop class mobo, non-ecc ram and an i5 or i7 processor (and less power draw, etc. etc.) It is also unclear how much performance gain/sacrifice I will see from this approach.

Can anyone provide me with some guidance, given my price range, or at least resources to go read on my own?  I greatly appreciate any assistance!

Adam

---

### Post by TheFu on 2017-08-15
Welcome to the forums.

I looked at making a VM server using those older Xeon CPUs which have been flooding the market.  The hard part for me was finding a quality, non-hated, motherboard.  I failed to find any for less than $500.  Looked for about 8 months beginning about a year ago.

I hope you had better luck than I did finding a good motherboard.

Servers are also noisy, heat generating, and power hungry - usually 3x the power that a solid desktop needs, sometimes 10x more power.  If you live in Alaska and need the heat, excellent!  If you live south of Ohio, maybe having another heater in the house/office for spring, summer and autumn isn't ideal.

Then Ryzen came out and I've been watching those CPUs.  The ryzen 5 1600 is 65W, cheap enough with excellent performance.  It should let me replace 3 of my current physical systems (core i5 and i7) which run about 20 VMs between them all.  There are 95W versions and more expensive versions.  The 1600 is just under $200, so ... 

I tend to spend $200 on a CPU, then get a new compatible motherboard and with Ryzen, I'd need new RAM (I hate forced RAM changes for 2% better performance).  DDR4 is still extremely expensive 2-3x more than DDR3. So I did a system build on paper and it was running $550 for a Ryzen 1600, 16G of cheap RAM and a mid-quality motherboard (X370).  I looked at the B320 and B350 MBs and decided they didn't fit my needs.  BTW, I generally buy $50 MBs, so going with the $150 one means the cheaper ones were lacking something I felt was very important for a VM server.  I would save by reusing a case, hdds, GPU, PSU, and everything else.  I'd add more RAM later, when DDR4 finally gets 75% less in cost.

Ryzen working with heavy loads and lots of threads have been segfaulting all summer.  AMD is aware if the issue. It isn't seen by many people, since they really don't push the systems hard at all.  That is common.  In fact, your workload doesn't sound like much at all.  I've started watching the Ryzen sales for CPU+MB+RAM combos, looking for something just around $400.

So ... you have to look at the total system performance when choosing hardware.  A used $230 desktop would be able to handle your workload easily.  Get an off-lease one from Microcenter.  Don't get a laptop - I/O matters and desktops, each cheap ones, blow away what laptops can handle.  For VM workloads, look for at least 4 cores.  You probably don't need more than 8G of RAM.

But if you really do need lots of I/O and processing - you're running a geospatial DB and doing 50 queries/second - then you'd want to spend the money on server-class I/O with multiple back planes and arrange the different SAS and NICs on different backplanes to spread the I/O out on all channels.  Look at the motherboard architecture diagram to see these things.  Desktops tend to have 1 backplane for most things and might have 1 for an SSD and one for the GPU, but everything else will share the same channels.  That means all USB traffic is stuck on the same backplane that all network traffic is on.   
I ran into this issue with my Core i5 desktop. The MB wasn't built to handle all the disk I/O and USB3 stuff I added.  Whenever I'm doing backups to a USB3 device, the system crawls because the same lanes are used for almost everything else - including SATA and GPU data.  It was never an issue with my external Infiniband disk array, but adding the USB3 addon-card (the MB is older than USB3), was just too much throughput for it.

And don't forget about CPU performance.  All benchmarks suck, but they are better than nothing when comparing vastly different hardware.  I use passmarks.  [www.cpubenchmark.net](www.cpubenchmark.net) has some.

You can look at pcpartpicker.com to see what others have done and which parts should be compatible.  Always search for "linux" with every component to see if others are having issues. For example, I know that realtek drivers and HW don't offload as much network I/O to the ASIC in the NIC as Intel NICs do, so I always want to use Intel NICs.  To me, it is worth the extra $20 to avoid the hassles from lesser NIC vendors.  At sustained near-GigE throughput, the CPU needed by a realtek NIC is 2-3x more than for an Intel NIC.  That may not matter to you.

Anyway, hope this is helpful on some level.

---

### Post by BenginM on 2017-08-15
Hiya Adam , welcome to the forums!

i use pcpartpicker it shows the Estimated Wattage as you add parts to the build list  , fo instance look at this build:

[https://pcpartpicker.com/list/WCnXcc](https://pcpartpicker.com/list/WCnXcc)

[https://pcpartpicker.com/list/dyw7LD](https://pcpartpicker.com/list/dyw7LD)

note the total Wattage estimated , So one would measure it and take into account for each part as taken the default cpu TDP some wattage for the motherboard , 1-2W per dimm , 2W per fan, 10W per hdd, and so on..

[https://en.wikipedia.org/wiki/Zen_(microarchitecture)#Server_processors](https://en.wikipedia.org/wiki/Zen_(microarchitecture)#Server_processors)

note also the better value CPUs on either side of Ryzen 5 1600 to 1400 & Ryzen 7 1700 (so to speak) have 
                      65W TDPs and happen to actually draw about that much power. and the AMD Epyc 7251 default TDP at 120W . but the old AMD server processors seems to have higher Wattages , but look at the Opteron A1100-series "Seattle" wattages ..

[https://en.wikipedia.org/wiki/List_of_AMD_Opteron_microprocessors#Opteron_6300-series_.22Abu_Dhabi.22_.2832_nm.29](https://en.wikipedia.org/wiki/List_of_AMD_Opteron_microprocessors#Opteron_6300-series_.22Abu_Dhabi.22_.2832_nm.29)


on my journey to build a desktop this week , i was told on freenode IRC that in generally it's preferred to get a power supply that is double the W of what the system consumes at 
                      full load at stock settings.. they only work at half load so they are quieter, and should have
                      room for expandability and you dont lose much cause of drop of efficiency at low 
                      loads ..

So you're talkin' about 
[https://www.amazon.com/Intel-E5-2670-2-60Ghz-8-Core-Processor/dp/B007H29FRS](https://www.amazon.com/Intel-E5-2670-2-60Ghz-8-Core-Processor/dp/B007H29FRS)
[https://ark.intel.com/products/64595/Intel-Xeon-Processor-E5-2670-20M-Cache-2_60-GHz-8_00-GTs-Intel-QPI](https://ark.intel.com/products/64595/Intel-Xeon-Processor-E5-2670-20M-Cache-2_60-GHz-8_00-GTs-Intel-QPI)

#See for example :

[https://pcpartpicker.com/list/mkY2yf](https://pcpartpicker.com/list/mkY2yf)

for ECC RAMs :

[https://www.newegg.com/Product/ProductList.aspx?Description=ECC%20RAM&Submit=ENE&IsNodeId=1&N=100007952%20601190337%20600564426%20600006161](https://www.newegg.com/Product/ProductList.aspx?Description=ECC%20RAM&Submit=ENE&IsNodeId=1&N=100007952%20601190337%20600564426%20600006161)

Now, if you want a dual Xeon E5-2670 CPUs you'll need a motherboard with dual-socket :

[https://pcpartpicker.com/product/nsjWGX/supermicro-x9drl-3f-atx-dual-cpu-lga2011-motherboard-x9drl-3f](https://pcpartpicker.com/product/nsjWGX/supermicro-x9drl-3f-atx-dual-cpu-lga2011-motherboard-x9drl-3f)

I don't know which of the desktop processors i7 -i5 you were referring to , weather Broadwell -E or skylake's 

[http://ark.intel.com/products/series/123588/Intel-Core-X-series-Processors](http://ark.intel.com/products/series/123588/Intel-Core-X-series-Processors)

look at 2620v4 , 2609v4 , 2608Lv4 , but the clock's speeds looks pathetic ..

[https://en.wikipedia.org/wiki/Broadwell_(microarchitecture)](https://en.wikipedia.org/wiki/Broadwell_(microarchitecture))

as for kaby-lake 

[https://en.wikipedia.org/wiki/Kaby_Lake](https://en.wikipedia.org/wiki/Kaby_Lake)

also, coffe lake will be released in a few days, but am not sure if there will be a server processors :

[https://en.wikipedia.org/wiki/Coffee_Lake](https://en.wikipedia.org/wiki/Coffee_Lake)

i use [http://cpuboss.com](http://cpuboss.com) to compare CPUs

---

### Post by BloodyIron on 2017-08-15
The biggest benefit you're going to notice about Xeon procs over consumer procs is the amount of RAM that you can use. I recommend that since this is for a server, that you go with Xeon, namely because it puts you in a better scenario for future growth.

Consumer CPUs are drastically more limited in how much RAM they can address, and this is intentional, so they sell more Xeons for your very purpose!

In your case going with lower-end or older Xeon CPUs is generally rather fine, especially first gen e5-2660 / 2670 procs. You'll get plenty of utility out of them!

---

