---
title: "Select components to build a new PC."
date: 2024-10-29
forum: Hardware
---

### Post by satimis on 2024-10-29
Hi all,

I'm going to build a new powerful desktop PC for home use.  I don't game neither WiFi is necessary.  The new PC will be connected direct to 1,000M up/down FTTH cable.

I have selected following components on searching Internet;

1.  Motherboard
ASUS PRIME B650M-A WIFI II DDR5,
Socket AM5 mATX Motherboard

Spec:
[https://www.asus.com/motherboards-components/motherboards/prime/prime-b650m-a/techspec/](https://www.asus.com/motherboards-components/motherboards/prime/prime-b650m-a/techspec/)

2. CPU
AMD Ryzen 7 8700F Processor 8C 16T Socket AM5

3. RAM
G.SKILL 64GB Kit (2x32GB) 
Ripjaws S5 Black F5-6400J3239G32GX2-RS5K 
DDR5 6400MHz Memory

4.  SSD Drive (2 drives)
4a.  (for Ubuntu Linux)
Samsung 2TB 990 EVO Plus MZ-V9S2T0BW M.2 2280 
PCIe 4.0 x4 / 5.0 x2 NVMe 2.0 SSD
(for virtualization)

4b.  (for Window 10 Home)
Samsung 1TB 990 EVO Plus MZ-V9S1T0BW M.2 2280 
PCIe 4.0 x4 / 5.0 x2 NVMe 2.0 SSD

What does it mean "5.0 x2 NVMe 2.0" ? 

5. Graphic card
4K graphic card already available
product: TU116 [GeForce GTX 1650 SUPER]
vendor: NVIDIA Corporation

6. Power supply already available (brand new)
Corsair (CXM series)
CX550
550 watt

The new PC shall run both Ubuntu Linux  and Window 10 Home systems, dual boot.  Virtualization (Oracle VirtualBox) will be installed on Ubuntu Linux drive.

I have no preset budget.  I need a powerful desktop PC for my use.

Please advise.  Thanks in advance

Regards

---

### Post by TheFu on 2024-10-29
Every 6 months, you seem to be building a new PC.  Care to explain?
You do realize that support for Win10 ends in less than 1 yr, right?

This system seems like overkill for "need a powerful desktop PC for my use."  A Ryzen 3 would be find for that and cost at least 50% less.  But if you just like to spend money, get a better GPU.  The Ryzen 7 power use is higher than Ryzen5 or lower CPUs, which can be seen in my electric bills.  Better for the environment to use less power.

Running 1 VM isn't anything that any computer made the last 10 yrs wouldn't handle just fine.  What, specifically, are you needing to run on this computer.

BTW, I have a Ryzen 5 and keep it pretty busy most of the time running 10+ containers and 7+ VMs while transcoding videos concurrently.
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        22Gi       2.4Gi       225Mi       5.7Gi       7.4Gi
Swap:         4.1Gi       2.6Gi       1.5Gi
```
And it is using only 22 GB of RAM.  Do you really need so much RAM?  There are reasons to have lots of RAM, but they are often tied to processing that also needs a $1500 GPU.

---

### Post by 1fallen on 2024-10-29
> **satimis said:**
> 

4b.  (for Window 10 Home)
Samsung 1TB 990 EVO Plus MZ-V9S1T0BW M.2 2280 
PCIe 4.0 x4 / 5.0 x2 NVMe 2.0 SSD

What does it mean "5.0 x2 NVMe 2.0" ? 


Seq. Read/Write (MB/s) Up to 5,000/4,200 performance. It's an amazing Drive, it's a shame to waste it on Windows though. :)

---

### Post by Dennis N on 2024-10-29
> What does it mean "5.0 x2 NVMe 2.0" ?
From the drive specs: PCIe 4.0 x4 / 5.0 x2 NVMe 2.0 SSD
It means the drive plugged into the PCIe 5.0 x4 slot will use 2 data lanes; if plugged into any PCIe 4.0 slot, it will use 4 data lanes. The net result is that the data transfer speed is the same*. You need a PCIe 5.0 x 4 drive to use all the lanes of the PCIe 5.0 x 4 slot to have faster data transfer.

*Either give 7.88 GB/s theoretical speed.

---

### Post by satimis on 2024-10-31
> **TheFu said:**
> Every 6 months, you seem to be building a new PC.  Care to explain?
You do realize that support for Win10 ends in less than 1 yr, right?

This system seems like overkill for "need a powerful desktop PC for my use."  A Ryzen 3 would be find for that and cost at least 50% less.  But if you just like to spend money, get a better GPU.  The Ryzen 7 power use is higher than Ryzen5 or lower CPUs, which can be seen in my electric bills.  Better for the environment to use less power.

Running 1 VM isn't anything that any computer made the last 10 yrs wouldn't handle just fine.  What, specifically, are you needing to run on this computer.

BTW, I have a Ryzen 5 and keep it pretty busy most of the time running 10+ containers and 7+ VMs while transcoding videos concurrently.
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        22Gi       2.4Gi       225Mi       5.7Gi       7.4Gi
Swap:         4.1Gi       2.6Gi       1.5Gi
```
And it is using only 22 GB of RAM.  Do you really need so much RAM?  There are reasons to have lots of RAM, but they are often tied to processing that also needs a $1500 GPU.
Hi TheFu,

Thanks for your advice.

I already have a AMD Ryzen 5 PC with 32G RAM onboard therefore for the new PC I upgrade it to AMD Ryzen 7 with 64G DDR5 RAM onboard.  I may consider building another AMD Ryzen 5 PC with 32G DDR5 RAM onboard.  I need PCIe 4.0 interface.  What will be your suggestion picking a new AMD Ryzen 5 CPU?

I have 42 websites running on Internet, hosted on HostGator server.  I will retain 42 cloned websites on the new PC as backup, as well as for testing new features to be added on the live sites.

Regards

---

### Post by satimis on 2024-10-31
> **1fallen2 said:**
> Seq. Read/Write (MB/s) Up to 5,000/4,200 performance. It's an amazing Drive, it's a shame to waste it on Windows though. :)
Hi 1fallen2,

Thanks for your comment.

I have old 1TB PCIe 3.0 SSD.  I may use it for installing Windows 10 Home or Windows 11.

Occasionally I run Windows.  Just as now OpenShot, both SNAP version and the version on Ubuntu repo, shutdown frequently running on Ubuntu 22.04 and 24.04.  I have to run it on Windows 10 Home.

Regards

---

### Post by satimis on 2024-10-31
> **Dennis N said:**
> From the drive specs: PCIe 4.0 x4 / 5.0 x2 NVMe 2.0 SSD
It means the drive plugged into the PCIe 5.0 x4 slot will use 2 data lanes; if plugged into any PCIe 4.0 slot, it will use 4 data lanes. The net result is that the data transfer speed is the same*. You need a PCIe 5.0 x 4 drive to use all the lanes of the PCIe 5.0 x 4 slot to have faster data transfer.

*Either give 7.88 GB/s theoretical speed.
Hi Dennis N,

Your advice noted and thanks

Regards

---

### Post by TheFu on 2024-10-31
> **satimis said:**
> Hi TheFu,

Thanks for your advice.

I already have a AMD Ryzen 5 PC with 32G RAM onboard therefore for the new PC I upgrade it to AMD Ryzen 7 with 64G DDR5 RAM onboard.  I may consider building another AMD Ryzen 5 PC with 32G DDR5 RAM onboard.  I need PCIe 4.0 interface.  What will be your suggestion picking a new AMD Ryzen 5 CPU?

I have 42 websites running on Internet, hosted on HostGator server.  I will retain 42 cloned websites on the new PC as backup, as well as for testing new features to be added on the live sites.

Regards

I have no recent recommendation for a Ryzen 5, just wondered why you seem to be upgrading PCs every 6 months.

BTW, the number of websites hosted elsewhere doesn't matter.  Having local copies is smart for the plans you want, but hosting 100 websites or 1000 is less about RAM/CPU and more about disk storage and bandwidth.  Of course, they type of programming language used for each website can have a big impact on CPU and RAM requirements, but the typical languages used outside a corporate environment are very efficient and having 5 or 500 php websites doesn't really matter. It is just a matter of storage.

You can run some simple numbers for concurrent users and bandwidth to see whether really fast SSDs are even needed.  Without real numbers, you are just guessing and might be spending money where it doesn't actually help, since the slow down will be networking, not storage.  If the SSD supports 32Gbps and you only have a 10 Gbps network connection, what's the point of adding faster disks?   There's also the real world performance capabilities. On disks, we tend to see the highest numbers for the theoretical, possible, bus, throughput, but at some point the data needs to be read from and written do the memory cells.  That will typically be orders of magnitude lower than the bus can support ... cough ... in theory.

There's nothing wrong with spending money on whatever you want for any reason you like too.  I just prioritize fast computing hardware lower and can easily find other things to spend the money on that would be higher on my priority list. To each their own.  I'll probably retain my current Ryzen 5600G systems for at least another 5 yrs, if not longer.  Generally, I want a 10x performance increase for $300 before I upgrade.  I might be able to get a 10x performance increase right now, but for over 10x the cost.  I can wait.

---

### Post by Yellow Pasque on 2024-10-31
> **satimis said:**
> I don't game

Then why bother with the Nvidia? I don't even think the 1650 can do AV1 decode, and you have to use hacky workarounds to get decode acceleration in the browser on Nvidia cards.
Get an 8700G. Call it a day. (The 8700G is very close to the 8700F except it's got graphics and a bit better stock cooler.)

---

