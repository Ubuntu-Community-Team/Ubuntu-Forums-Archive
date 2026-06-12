---
title: "Seeking advice for building a new PC"
date: 2019-10-12
forum: Hardware
---

### Post by satimis on 2019-10-12
Hi all,

I haven't built PC, at least, for more than 10 years.  I suppose it is time to build a new PC replacing my daily working one.

My Daily working PC:
AMD 8-core
RAM 32G
(will be as spare/stand-by PC)

Spare PC:
AMD 8-core
RAM 8G
(will retire)

My preliminary config for this new PC is as follows;

1. CPU
AMD Ryzen 5 3600 100-100000031BOX 6C/12T, 3.6GHz,35MB Cache, Socket AM4 CPU BOX w/Cooler	

2. Motherboard```

Budget X570: ASUS Prime X570-P
ASUS PRIME X570-P/CSM X570,AM4 Socket,USB3.2,PCIe 4.0 M.2 ATX M/B

```
Specifications
[https://www.asus.com/Motherboards/PRIME-X570-P/specifications/](https://www.asus.com/Motherboards/PRIME-X570-P/specifications/)

(I suppose not necessary to add a graphic card)

3. RAM 64G```

Corsair Mac DDR-4 2666MHz 64GB Kit (4x16G) SODIMM Memory CMSA64GX4M4A2666C18 Apple Certified
```
TECH SPECS
[https://www.corsair.com/tw/en/Categories/Products/Memory/Mac-Memory/p/CMSA64GX4M4A2666C18#tab-tech-specs](https://www.corsair.com/tw/en/Categories/Products/Memory/Mac-Memory/p/CMSA64GX4M4A2666C18#tab-tech-specs)


Reference
========
AMD Ryzen 5 3600 review
[https://www.techradar.com/reviews/amd-ryzen-5-3600](https://www.techradar.com/reviews/amd-ryzen-5-3600)

Best Motherboards for AMD Ryzen 5 3600X in 2019
[https://www.windowscentral.com/best-motherboards-amd-ryzen-5-3600x](https://www.windowscentral.com/best-motherboards-amd-ryzen-5-3600x)


Comment and suggestion would be appreciated.  (I have no pre-set budget)

Thanks in advance.

Regards
satimis

---

### Post by TheFu on 2019-10-12
You need a GPU with the 3600X, unless you do all sorts of stuff to have a serial console.

Last December, I build an Asus B450 with a Ryzen 2600.  It is about 30% cheaper to build that system today than it was back then.  I've considered building a spare Ryzen 1600 multiple times, since a 1600 is only US$80 locally. Think I could get the MB+CPU+RAM for less than $200.

I do agree on the Ryzen choice, not sure I'd get the 3xxx CPU. Current generation is always more costly for only modest gains over the last generation. 
3600x - $200
3600 - $180
2600 - $115
1600 - $80
The "x" means 95W of power.  The non-X means 65W of power.  That's important to me for cooling and quiet.
You can look up the passmarks for each to help decide if the extra price is worth the higher performance.

I couldn't imagine needing more than 16G of RAM, but I don't use Windows and only need to host about 20 VMs, mostly servers.

I do require the motherboard NIC be intel and not have wifi.  It just isn't worth my time to hassle with other NICs over $20 price differences. Plus, Intel NICs are well supported by BSD.

---

### Post by satimis on 2019-10-13
> **TheFu said:**
> You need a GPU with the 3600X, unless you do all sorts of stuff to have a serial console.
Please explain in more detail.  Whether you suggested not going to motherboard with onboard graphic card?    Thanks.

> 
Last December, I build an Asus B450 with a Ryzen 2600.  It is about 30% cheaper to build that system today than it was back then.  I've considered building a spare Ryzen 1600 multiple times, since a 1600 is only US$80 locally. Think I could get the MB+CPU+RAM for less than $200.

I do agree on the Ryzen choice, not sure I'd get the 3xxx CPU. Current generation is always more costly for only modest gains over the last generation. 
3600x - $200
3600 - $180
2600 - $115
1600 - $80
The "x" means 95W of power.  The non-X means 65W of power.  That's important to me for cooling and quiet.
You can look up the passmarks for each to help decide if the extra price is worth the higher performance.
The reason for me looking at "AMD Ryzen 5 3600" is it having "35MB Cache".  But "AMD Ryzen 5 2600" only with "19MB Cache"

```

AMD Ryzen 5 2600 YD2600BBAFBOX 6C/12T, 3.9GHz, 19MB Cache, Socket AM4 CPU BOX w/Cooler

AMD Ryzen 5 3600 100-100000031BOX 6C/12T, 3.6GHz,35MB Cache, Socket AM4 CPU BOX w/Cooler

```
The speed of :AMD Ryzen 5 2600" is faster, 3.9GHz

> 
I couldn't imagine needing more than 16G of RAM, but I don't use Windows and only need to host about 20 VMs, mostly servers.

The RAM usuage of my daily working PC (32G RAM)

No VMs running
&#10219; free -m```

              total        used        free      shared  buff/cache   available
Mem:          32067        1467       29411         213        1188       29957
Swap:           975           0         975

```

5 VMs running (1 Windows and 4 Ubuntu)
&#10219; free -m```

              total        used        free      shared  buff/cache   available
Mem:          32067       11623       19029         238        1414       19681
Swap:           975           0         975

```

10 VMs running (2 Windows and 8 Ubuntu)
&#10219; free -m```

              total        used        free      shared  buff/cache   available
Mem:          32067       27450        3045         257        1572        3700
Swap:           975           0         975

```
dropping to free=3045.

I have about 30 VMs installed but not all running at the same time.  Therefore I consider to install 64G RAM.  Windows here is only for testing, not always up

Other advice noted with thanks

Regards
satimis

---

### Post by satimis on 2019-10-13
> **TheFu said:**
> You need a GPU with the 3600X, unless you do all sorts of stuff to have a serial console.
Please explain in more detail.  Whether you suggested not going to motherboard with onboard graphic card?    Thanks.

> 
Last December, I build an Asus B450 with a Ryzen 2600.  It is about 30% cheaper to build that system today than it was back then.  I've considered building a spare Ryzen 1600 multiple times, since a 1600 is only US$80 locally. Think I could get the MB+CPU+RAM for less than $200.

I do agree on the Ryzen choice, not sure I'd get the 3xxx CPU. Current generation is always more costly for only modest gains over the last generation. 
3600x - $200
3600 - $180
2600 - $115
1600 - $80
The "x" means 95W of power.  The non-X means 65W of power.  That's important to me for cooling and quiet.
You can look up the passmarks for each to help decide if the extra price is worth the higher performance.
The reason for me looking at "AMD Ryzen 5 3600" is it having "35MB Cache".  But "AMD Ryzen 5 2600" only with "19MB Cache"

```

AMD Ryzen 5 2600 YD2600BBAFBOX 6C/12T, 3.9GHz, 19MB Cache, Socket AM4 CPU BOX w/Cooler

AMD Ryzen 5 3600 100-100000031BOX 6C/12T, 3.6GHz,35MB Cache, Socket AM4 CPU BOX w/Cooler

```
The speed of :AMD Ryzen 5 2600" is faster, 3.9GHz

> 
I couldn't imagine needing more than 16G of RAM, but I don't use Windows and only need to host about 20 VMs, mostly servers.

The RAM usuage of my daily working PC (32G RAM)

No VMs running
&#10219; free -m```

              total        used        free      shared  buff/cache   available
Mem:          32067        1467       29411         213        1188       29957
Swap:           975           0         975

```

5 VMs running (1 Windows and 4 Ubuntu)
&#10219; free -m```

              total        used        free      shared  buff/cache   available
Mem:          32067       11623       19029         238        1414       19681
Swap:           975           0         975

```

10 VMs running (2 Windows and 6 Ubuntu)
&#10219; free -m```

              total        used        free      shared  buff/cache   available
Mem:          32067       27450        3045         257        1572        3700
Swap:           975           0         975

```
dropping to free=3045.

I have about 30 VMs installed but not all running at the same time.  Therefore I consider to install 64G RAM.  Windows here is only for testing, not always up

Other advice noted with thanks

Edit
===
Just found;
Best Graphics Cards to Pair With the Ryzen 5 3600
[https://premiumbuilds.com/graphics-cards/best-gpu-for-ryzen-5-3600/](https://premiumbuilds.com/graphics-cards/best-gpu-for-ryzen-5-3600/)

Regards
satimis

---

### Post by Dennis N on 2019-10-13
> Please explain in more detail. Whether you suggested not going to motherboard with onboard graphic card? Thanks.
Integrated graphics are part of the CPU. The CPU you are considering doesn't have integrated graphics, so you need a separate (discrete) graphics card.

---

### Post by TheFu on 2019-10-13
Integrated GPUs are on the CPU, not the motherboard.  If you intend to have a Ryzen with an iGPU, then get a model that ends in 'g' .... 2200g, 2400g, 3200g, 3400g .... you get the idea.  You can google for the specific APUs which come with an iGPU. AMD calls their CPUs with GPUs onboard, "APUs", sometimes.

Clock speed doesn't related to performance and hasn't since the 1990s, unless everything else is identical.  That's where benchmarks come in and why there are benchmarks for different sorts of workloads.  Lacking any specific workload, I use *passmark*, but use whatever you like.

The Ryzen 3xxx series needs chipset support to take advantage of some of the newer performance enhancements.  While my B450 motherboard will work, only specific models of the higher cost X5xx series MBs.  I'm not in the market, so don't recall the details, but I think the X570 is one that does.  Good choice, but please verify.

There is no "right" answer and we can't know all the important things for your needs.  Perhaps I'm more price sensitive than you are?

---

### Post by satimis on 2019-10-14
> **Dennis N said:**
> Integrated graphics are part of the CPU. The CPU you are considering doesn't have integrated graphics, so you need a separate (discrete) graphics card.
Hi,

Thanks for your advice.

But I couldn't resolve, it mentioning on;
[https://www.asus.com/Motherboards/PRIME-X570-P/specifications/](https://www.asus.com/Motherboards/PRIME-X570-P/specifications/)
```

Graphic
Integrated Graphics in the 2nd and 1st Gen AMD Ryzen™ with Radeon™ Vega Graphics Processors
VGA output support : HDMI port
- Supports HDMI 1.4b with max. resolution 4096 x 2160 @ 24 Hz

```
Besides there is a HDMI port on the motherboard
PRIME X570-P
[https://www.asus.com/Motherboards/PRIME-X570-P/](https://www.asus.com/Motherboards/PRIME-X570-P/)

It supports 4K resolution.  That is OK.  I only have 25" 3K display which have been running for >10 years and I'm considering to purchase a 30"/32" 4K display.  My table doesn't have a head room for 40" display.  There is a overhead cabinet.

However it doesn't mention the memory 1G/4G or 6G

I prefer separate graphic card rather than onboard graphic card.  I'm now searching an equivalent motherboard instead of disabling the onboard graphic card on PRIME X570-P.

Regards
satimis

---

### Post by satimis on 2019-10-14
> **TheFu said:**
> Integrated GPUs are on the CPU, not the motherboard.  If you intend to have a Ryzen with an iGPU, then get a model that ends in 'g' .... 2200g, 2400g, 3200g, 3400g .... you get the idea.  You can google for the specific APUs which come with an iGPU. AMD calls their CPUs with GPUs onboard, "APUs", sometimes.

Clock speed doesn't related to performance and hasn't since the 1990s, unless everything else is identical.  That's where benchmarks come in and why there are benchmarks for different sorts of workloads.  Lacking any specific workload, I use *passmark*, but use whatever you like.

The Ryzen 3xxx series needs chipset support to take advantage of some of the newer performance enhancements.  While my B450 motherboard will work, only specific models of the higher cost X5xx series MBs.  I'm not in the market, so don't recall the details, but I think the X570 is one that does.  Good choice, but please verify.

- snip -
Thanks for your advice.

On
ASUS website
[https://www.asus.com/Motherboards/PRIME-X570-P/HelpDesk_CPU/](https://www.asus.com/Motherboards/PRIME-X570-P/HelpDesk_CPU/)

PRIME X570-P suports```

Ryzen 5 3600 (3.6GHz,65W,L3:32M,6C,B0)

```

On Memory supported
[https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/PRIME_X570-P/Memory_QVL_2nd_Gen_AMD_Ryzen_Radeon_Graphics_X570_0730.pdf](https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/PRIME_X570-P/Memory_QVL_2nd_Gen_AMD_Ryzen_Radeon_Graphics_X570_0730.pdf)

I couldn't find```

Corsair Mac DDR-4 2666MHz 64GB Kit (4x16G) SODIMM Memory CMSA64GX4M4A2666C18 Apple

```

I'm now contacting ASUS Support to check whether "PRIME X570-P' support this module

Regards
satimis

---

### Post by CatKiller on 2019-10-14
> **satimis said:**
> I'm now searching an equivalent motherboard instead of disabling the onboard graphic card on PRIME X570-P.

You still seem confused on this point. The motherboard doesn't provide any graphics: the processor does.

The processors that have graphics and the processors that don't both use the same sockets and work in the same motherboards. The motherboard needs some way to get the signal from the processor to the monitor; that's what you were reading about.

---

### Post by satimis on 2019-10-14
> **CatKiller said:**
> You still seem confused on this point. The motherboard doesn't provide any graphics: the processor does.

The processors that have graphics and the processors that don't both use the same sockets and work in the same motherboards. The motherboard needs some way to get the signal from the processor to the monitor; that's what you were reading about.
Hi,

Thanks for your advice.

I'm now clear after reading your advice as well as following thread in combination.

Must a CPU have a GPU if the motherboard provides a display port (when there isn't any separate video card)?
[https://superuser.com/questions/1447318/must-a-cpu-have-a-gpu-if-the-motherboard-provides-a-display-port-when-there-isn](https://superuser.com/questions/1447318/must-a-cpu-have-a-gpu-if-the-motherboard-provides-a-display-port-when-there-isn)

Therefore I have to select```

AMD Ryzen 5 3400G YD3400C5FHBOX 4C/8T, 3.7GHz,6MB Cache, Socket AM4 CPU BOX w/Cooler
```

The price is cheaper but its Cache is only 6MB.

```

AMD Ryzen 5 3600 100-100000031BOX 6C/12T, 3.6GHz,35MB Cache, Socket AM4 CPU BOX w/Cooler

```
AMD Ryzen 5 3600 with 35MB Cache.

Does it matter?

Regards
satimis

---

### Post by TheFu on 2019-10-14
These questions have been answered above. Please re-read.
BTW, SODIMM RAM is for laptops, not desktop motherboards.

I'm loath to attempt any more answers, since it seems confusing based on the replies.  Perhaps pcpartpicker.com would be helpful?

---

### Post by CatKiller on 2019-10-14
> **satimis said:**
> Must a CPU have a GPU if the motherboard provides a display port (when there isn't any separate video card)?


You'll need *something* to provide graphics. Either a GPU as a separate card or a GPU integrated into the processor. Whether you need a dedicated GPU or whether an integrated GPU will be adequate for your needs is something that only you can answer. There are plenty of reviews around that compare the performance of the integrated GPUs with popular dedicated ones. If you have integrated graphics now and decide that you need a dedicated GPU later you can simply turn off the integrated one.

---

### Post by satimis on 2019-10-14
> **CatKiller said:**
> You'll need *something* to provide graphics. Either a GPU as a separate card or a GPU integrated into the processor. Whether you need a dedicated GPU or whether an integrated GPU will be adequate for your needs is something that only you can answer. There are plenty of reviews around that compare the performance of the integrated GPUs with popular dedicated ones. If you have integrated graphics now and decide that you need a dedicated GPU later you can simply turn off the integrated one.
Thanks for your advice.

What I'm prepared to do is;
1) Purchase
ASUS PRIME X570-P motherboard
and
AMD Ryzen 5 3400G YD3400C5FHBOX 4C/8T, 3.7GHz,6MB Cache, Socket AM4 CPU BOX w/Cooler

AMD Ryzen&#8482; 5 3400G with Radeon&#8482; RX Vega 11 Graphics
[https://www.amd.com/en/products/apu/amd-ryzen-5-3400g](https://www.amd.com/en/products/apu/amd-ryzen-5-3400g)

I suppose it works without a graphic card.  

2) If NOT I just purchase a graphic card.

Now I'm still searching around RAM to work on ASUS PRIME X570-P motherboard.  I need 64G RAM

Regards
satimis

---

### Post by ajgreeny on 2019-10-14
Not saying you're wrong, but you say you "need 64G RAM".

Are you certain? That's an enormous amount and way more than is needed by most users.

---

### Post by CatKiller on 2019-10-14
> **satimis said:**
> Now I'm still searching around RAM to work on ASUS PRIME X570-P motherboard.

The Qualified Vendor List (all the modules that the manufacturer has specifically tested) for that motherboard is [here.]("https://www.asus.com/Motherboards/PRIME-X570-P/HelpDesk_QVL/") Note the last column: not all kits will work at the fastest speed with 4 modules.

64 GB is an awful lot of RAM.

---

### Post by QIII on 2019-10-14
Unless you are doing heavy scientific calculation or running a significant number of virtual machines, it is not at all likely that you need 64GB of RAM. 

Is that what you are doing?

For the vast majority of users, even 16GB is overkill.

---

### Post by satimis on 2019-10-14
Hi all,

Lot of thanks for your advice and comment.

From the list of ASUS Memory Supported;
[https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/PRIME_X570-P/Memory_QVL_2nd_Gen_AMD_Ryzen_Radeon_Graphics_X570_0730.pdf](https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM4/PRIME_X570-P/Memory_QVL_2nd_Gen_AMD_Ryzen_Radeon_Graphics_X570_0730.pdf)

I found following memory```

Corsair	 CMK64GX4M4B3000C15(Ver4.31)	4*16GB	DS	Samsung
	         CMK64GX4M4A2666C16(Ver5.3)	        4*16GB	DS	Hynix
	         CMW32GX4M2Z3200C16(Ver3.31)	2*16GB	DS	Hynix
	         CMD32GX4M2B3000C15(Ver4.31)	2*16GB	DS	na
	         CMU32GX4M2A2666C16(Ver5.20)	2*16GB	DS	Samsung
HyperX	 HX429C17FBK4/64		                4*16GB	DS	Micron
	         HX430C15PB3AK4/6	                        4*16GB	DS	Hynix
G.SKILL	 F4-2400C15Q-64GIS	                        4*16GB	DS	Micron
	         F4-2400C15Q-64GFX	                        4*16GB	DS	Hynix
	         F4-2400C16Q-64GFX	                        4*16GB	DS	Hynix

```

I have >30 VMs (Windows/Ubuntu/Debian etc) installed but not all running at the same time.  My daily working PC with 32G RAM installed has been running >10 years without problem.  My thought is for a new PC I need increasing the RAM size OR at least not less than the current PC.  AH maybe I would install 32G RAM first.

My daily working PC is still working and the only problem is hanging occasionally.  I suppose the components need to be cleaned thoroughly, in particular, the contact surface of the CPU and its cooling fan.  Also it is the time for it to retire as a stand-by PC.

Regards
satimis

---

