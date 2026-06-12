---
title: "Best driver for intel graphics card in Ubuntu 14.04?"
date: 2015-08-18
forum: Hardware
---

### Post by Riemens on 2015-08-18
Hey,

I play Team Fortress 2, fps is really low and choppy. I believe my pc is good enough for running this game properly. Am I using the right driver or is there a better one out there?

My specs:
Laptop Aspire E5
Processor: Intel Core I5-4210U CPU @ 1.70GHz x 4
Graphics: Intel Haswell Mobile
OS type: 64-bit

When I run this command: sudo lshw -C video
 *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:62 memory:b0000000-b03fffff memory:a0000000-afffffff ioport:4000(size=64)

When I run this command: [COLOR=#111111][FONT=Consolas]lspci | grep VGA
[/FONT][/COLOR]00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)



I hope that was enough information. I'm new to Ubuntu (and Linux).

Is there a better driver for this graphics card, or is it really that bad?

Thanks.

---

### Post by astralnysledz on 2015-08-19
Firstly, you have an ultrabook-class processor. Although it's i5, it's clocked at 1.7 GHz per core. I have a similar Asus S301 ultrabook, though with Intel i3. This will greatly affect performance in games.

Secondly, the only driver that we have for Intel integrated iGPUs is the not-so-efficient mesa/galium 3D open-source driver. Fully proprietary Intel graphics drivers are not available for Linux. To top it off, by default those drivers function in some sort of power-saving mode to prevent overheating and hardware damage. This can probably be changed in the kernel, but I do not know how, sorry.

As a case in point, I compared the way Goat Simulator runs on my Asus S301 ultrabook and an old Macbook Pro (unibody) 2008.

MacBook Pro (unibody) 2008:
Intel Core 2 Duo @ 2.4 GHz x 2
Nvidia Geforce 320M graphics + proprietary drivers (340 branch)
4 GB RAM 1066 MHz

Asus S301 ultrabook:
Intel Core i3 @ 1.7 GHz x 2 ( x 2 more for hyper-threading)
Intel HD 4400
4 GB RAM 1600 MHz

Since I'm mentioning everything, one can already guess that because of the drivers difference the MacBook Pro handles Goat Simulator much better, though it overheats tremendously at the same time.

---

### Post by SeijiSensei on 2015-08-19
I'm not sure what a "proprietary" adapter for Intel graphics might be, since [Intel itself wrote the open-source driver]("https://01.org/linuxgraphics") that appears in the Linux kernel.

---

### Post by astralnysledz on 2015-08-19
> **SeijiSensei said:**
> I'm not sure what a "proprietary" adapter for Intel graphics might be, since [Intel itself wrote the open-source driver]("https://01.org/linuxgraphics") that appears in the Linux kernel.

What I wanted to point out in my previous post was that open-source Intel graphics drivers rely on Gallium3D libraries (sorry for a typo in my earlier post), rather than on their own proprietary components. Gallium3D is also used by the open-source nouveau and radeon drivers. Phoronix has done multiple benchmark comparisons across various Linux distributions, driver setups (open-source vs proprietary), Windows vs Linux, etc. In those Gallium3D always came out short.

However, I suspect that OPs problem with performance may also be attributed to the processor.

---

### Post by Riemens on 2015-08-20
> **astralnysledz said:**
> Firstly, you have an ultrabook-class processor. Although it's i5, it's clocked at 1.7 GHz per core. I have a similar Asus S301 ultrabook, though with Intel i3. This will greatly affect performance in games.


Do you mean that my processor is too slow or that it's a good one ("ultrabook-class processor" sounds good).

**Luckily I managed to get steam-login to work again (reinstalled everything). Game runs smooth again**, I'll never touch my Ubuntu machine again :)

Problem solved.

Thanks for the replies.

Sorry for my lack of basic computer knowledge :/.

---

### Post by SeijiSensei on 2015-08-21
> **astralnysledz said:**
> In those Gallium3D always came out short.

I see.  I don't care about 3D performance since I don't game in Linux.

---

