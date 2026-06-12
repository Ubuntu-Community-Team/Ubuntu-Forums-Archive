---
title: "DIY High Performance VMWare PC"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by water8 on 2007-10-13
I am working to build a cost effective DIY PC to run VMWare server for software testing purpose. Since I need to run quite a number of VMware instances, I am thinking to have the machine with 8G Ram. 

For performance, the linux system will be running in command mode without graphic.

Some questions :-

1.	For the same money spending, should I consider AMD2-64 or Intel Core2Duo ?
2.	I am thinking to use the Ubuntu 64bit Linux to run the VMware Server, any comment?
3.	Is that correct I must use the 64bit OS to access the 8G ram?
4.	I heard rebuild the Linux kernel can improve the performance, how much percent could be fast if I optimized the kernel for running VMWare server?
5.	For the DIY Machine, how much faster for 800 vs 667 RAM?
6.	Would it be hard to over clock the 800 to 1000 without losing the stability, and how much faster could it be?
7.	My initial thinking is to use AMD2-64 at 4000 up to 4800. How much faster could it be? Without losing the stability, how much faster can I over clock the CPU? 
8.	I am thinking the Asus M2N-MX or M2A-VM microATX motherboard, any comment?
9.	How much would the disk access be faster if I can find a lowcost motherbaord providing Raid 0 for 2 x Seagate 160M harddrive?

Any comment will be helpful and welcome!

Thanks a million.

---

### Post by Wall86 on 2007-10-13
I do not know to much about setting up the VMWare but I can tell ya about performance and overclocking. 

First of all, since this will be a server I do not recommend using an AMD Athlon socket AM2, ya wanna use an Opteron, it is more cost effective for power usage etc.... 

Also ,since thsi is a dedicated server you will be needing Fully Buffered RAM, this is quite a bit more expensive, but is worth it for dedicated servers as errors can throw ya through a loop. 


If you do decide to go with an Athlon, I recommend going with a 6000 or 6400, with current prices sitting around $169 CAD for the 6000 and $229 for the 6400+. If you do wanna overclock I would suggest the 6400 as it is an unlocked multiplier CPU (you just have to buy an aftermarket heatsink)

for the regular memury (unbuffered) I have seen some decent dual channel kits from OCZ for under $100 for 2 GB of pc2-667. I picked up my 2 GB kit of crucial Ballistix Tracer for $179, but that is pc2-800 and SLI compliant. I would nto suggest going over the PC2-800 specs for an Athlon as the memory controller on chip is mostly designed for a maximum of 800 Mhz memory, the gains of a higher memory clock are negligible at best, what ya wanan look at is lower latencies on the memory (5-5-5-15 is decent, but lower the better) 

also, I can not guarntee overclocking results, as it does depend on the part in question.

---

### Post by water8 on 2007-10-13
Thanks for the input.

The purpose of building this DIY pc is for a portable idea for system testing, and customer demo. Currently, I am using 5 low cost Linux PCs  (AMD2-64/4G Ram+VMWare server) to test a system consists lot servers and clients.

Same here, 2G/667 or 800 ram is also getting affordable, it is possible to have 2x4=8GRAM in a light weight PC case using microATX motherboard so that I can hand carry few of them.

Stability is not on the top of the concern because this is for not for production. Budget is constraint, and need to think the better use of money. Performance is important because more virtual systems are now running after adding ram, some ideas are :-

1)     optimize the Ubuntu by rebuild the kernel(totally free)
2)     buying AMD2 4800 or even faster CPU
3)     using 2 HDD in raid 0 (many motherboard build-in this, but at lower performance)
4)     over clock the ram (free of money, but at the cost of stability)
5)     over clock the CPU ( free of money, but at the cost of stability)

I also noticed some website saying Intel core2duo is a lot faster than AMD. So I need helps to rethink if AMD is still the cost effective option. Any comment?

---

### Post by water8 on 2007-10-20
Finally, I built 2 servers, and both of them running Ubuntu 64bit, VMWare server 1.04.

server 1:  GA-G33M-S2H, E6550, A-data/800 4G, Seagate 250G, MiniCase at $540
server 2: ASUS M2A-VM, AMD5000+, A-data/800 4G, Seagate 250G, MiniCase at $420

Basically, I hardly notice any performance differece between 2 systems. I believe this is because the server function depends mostly on Harddisk and Ram speed.

I downloaded the unixbench, and the results are 468.4, 375.3 respectively. Intel is faster.

---

