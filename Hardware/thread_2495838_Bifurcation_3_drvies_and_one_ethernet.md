---
title: "Bifurcation 3 drvies and one ethernet?"
date: 2024-03-03
forum: Hardware
---

### Post by josephchrzempiec on 2024-03-03
Hello, I'm not sure if this is in the right place or not. I have a server motherboard that I have a server that has Bifurcation with ubuntu on it. So far everything works. One thing I'm missing is I need 10GB ethernet. So far I have 2 nvme drives connected. I don't don't know if anyone has done this before and Wanted to know If it is possible to use the last 4 lanes for the 10GB ethernet card? I have ordered a 10GB ethernet card and it's on the way But I'm curious if it will work If anyone has tried to get something like this work.

Joseph

---

### Post by MAFoElffen on 2024-03-04
Bifurcation is "tricky" currently.

It is new technology, and there is no standard between vendors. When helping people with it, I need to know exactly which vendors and motherboard model and revision.

Why? Because each vendor implements it differently, and even then... They will change little things for each model and revision.

They bury things within the User manual. Like if you use this kind of device in this slot or port, it will disable this other slot or port somewhere else.Or if you use a PCIe Gen5 in certain slot, then it downgrade other PCIe slots to Gen4. 

For instance mine, where if I use an NVMe in M2_3, it disables SATA_7 and makes it unavailable. Or other, where some M.2 NVMe slots are PCIe & SATA, and some are only SATA... Or if you put a Gen5 GPU in a certain slot.... affecting which bus they are on, and the speeds the other slots, and how many lanes are left to use.

Even then, with what the User Manual says, some Users still had to call the Vendor's Support to clarify, what their board really does, in some instances. Yet I still had one user, where the User Manual said one thing, and what was in reality was different.

So what I can say, it depends.

---

### Post by josephchrzempiec on 2024-03-04
[COLOR=#000000][INDENT]A Friend of mine gave me a Supermicro motherboard. He had 3 of these at his work. They phases them out and he bought them from his work while they upgraded to newer boards and sold them on the used to my friend.

The mother board model is X10SDV-4C-TLN2F. That can be found here [https://www.supermicro.com/en/produc...10SDV-4C-TLN2F]("https://www.supermicro.com/en/products/motherboard/X10SDV-4C-TLN2F") . It is a 4 core 8 threads and even used they are costly. It has a Gen3 16x slot with Bifurcation. I did look up the manual and had a fun time trying to figure out how Bifurcation works. With a little help of google and come people in here plus youtube. I manage to get it working.[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by josephchrzempiec on 2024-03-04
Hello, I'm sorry I messedup I only have 2 drives connected not 3. And I looked through the manual and missed something. It is only an 8x8 bifurcation only. This is my mistake.

---

### Post by MAFoElffen on 2024-03-05
You said Gen3... 
> 
PCIe Gen 3 operates at 8 GT/s (gigatransfers per second) which roughly translates to 1 GB/s per PCIe lane. By comparison, PCIe Gen 4 operates at 16 GT/s, or around 2 GB/s (gigabytes per second) per PCIe lane.

You want to do Ethernet 10GT/s... Actually. this article says you only need 4 lanes of gen 3 to do that, because of data compression: [https://www.genuinemodules.com/how-many-pcie-lanes-for-10gb-ethernet_a7905](https://www.genuinemodules.com/how-many-pcie-lanes-for-10gb-ethernet_a7905)
> 
In general, a 10Gb Ethernet network adapter requires at least one PCIe lane to function. However, to fully utilize the 10Gb bandwidth, it is recommended to use a network adapter that supports PCIe Gen3 x4 or higher.

Single port Ethernet 10G cards are usually PCIe x4 slots...

I looked at that link you posted for that board's specs. Are you sure you posted the right link? It says it already has two 10G Ethernet ports. It also says 1 PCIe x16 slot and "only" 1 M.2 slot, and 6 SATA slots? 

I think I'm confused by what you said you have installed on it, and what you want to do.

In the one x16 slot... If you had their optional PCIe Riser card, then it would use bifurcation in the BIOS to split the lanes into the two x8 slots... (it doesn't do much more than that) 
> 
SLOT 7 PCI-E 3.0 X16 Bifurcation
Use this feature to set the PCI-E slot to operate as a sinlge x16 slot or to bifurcate
into two x8 slots. A proper riser card must be used to take advantage of bifurication.
The options are x8x8 and x16

You could use one of those x8 slots for a 10G Ethernet card.

---

### Post by josephchrzempiec on 2024-03-05
> **MAFoElffen said:**
> You said Gen3... 

You want to do Ethernet 10GT/s... Actually. this article says you only need 4 lanes of gen 3 to do that, because of data compression: [https://www.genuinemodules.com/how-many-pcie-lanes-for-10gb-ethernet_a7905](https://www.genuinemodules.com/how-many-pcie-lanes-for-10gb-ethernet_a7905)

Single port Ethernet 10G cards are usually PCIe x4 slots...

I looked at that link you posted for that board's specs. Are you sure you posted the right link? It says it already has two 10G Ethernet ports. It also says 1 PCIe x16 slot and "only" 1 M.2 slot, and 6 SATA slots? 

I think I'm confused by what you said you have installed on it, and what you want to do.

In the one x16 slot... If you had their optional PCIe Riser card, then it would use bifurcation in the BIOS to split the lanes into the two x8 slots... (it doesn't do much more than that) 

You could use one of those x8 slots for a 10G Ethernet card.


I was thinking the same thing. I have an nvme bootdrive really doing nothing but running a couple of tasked. I was thinking of moving the boot drives to sata and put a pair of them in raid just incase.
and keeping the the pair of nvme drives that is on The [COLOR=#000000]Bifurcation card and leave it alone. However I do have a nvme to 4x pcie slow cable and adapter. On the left end of the case there is no motherboard on the last 2 slots I can put a 10GB ethernet card with that adapter on it. Becuase the motherboard is shorter then the case itself so the end of the motherboard comes up to just before the last 2 slots at the back of the case. So i can put something there like that cable and adapter there for a 10Gb and yes I do have a 10GB card I would love to put there.

You are correct on all accounts Thank you.
[/COLOR]

---

### Post by MAFoElffen on 2024-03-07
I am curious. The pictures in the manual only show one NVMe slot, and one single PCIe x16 slot. Could you post/attach a photo of the board?

---

