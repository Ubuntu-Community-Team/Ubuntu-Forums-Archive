---
title: "New build, AMD questions"
date: 2017-02-06
forum: Hardware
---

### Post by robbie 348 on 2017-02-06
I'm thinking of upgrading my pc and AMD seem to have better value for money (cheaper, like me) in both motherboards and cpu's over intel.However, I keep reading about AMD issues and wonder if it's worth it or just stay with intel? I'm not playing games etc, just basic stuff on Ubuntu 16.04, so no need for a graphics card. Am I correct in assuming that stock drivers would be OK? Looking at something like this AMD A4-7300 with AMD Radeon HD 8470D Graphics on an Asus A88XM-E board.
Any and all opinions/advice welcome.
Thanks, Rob.

---

### Post by Autodave on 2017-02-06
Since you asked for opinions, here are mine. Nvidia graphics is just the easiest to work with.  Also, I have seen many posts about issues w/Asus: most seem to be corrected eventually, but.......

---

### Post by robbie 348 on 2017-02-06
Thanks, kinda thinking the same thing

---

### Post by mastablasta on 2017-02-06
AMD is ok if you use the ones with GCN. they get updates and such and use opensource drivers. so later models are a bit better supported. various tests are available. and mostly desktop with AMD is working, it's just gaming that is giving issues. sometimes. not always.

but you do not need to go with APU. you can get descent AMD CPU (no GPU on it) slightly weaker than i5 and much cheaper. then add nVidia card to it.

---

### Post by robbie 348 on 2017-02-07
you can get descent AMD CPU (no GPU on it) slightly weaker than i5 and much cheaper. then add nVidia card to it. 				
Thanks for the tip. I never knew you could mix Nvidia and AMD, Rob.

---

### Post by gordintoronto on 2017-02-09
I'm running an AMD Phenom II X2 with nVidia video card. Over eight years, the Gigabyte motherboard has been the source of a couple of issues, but overall I'm delighted with the price/performance.

I made heavy use of reviews on Newegg to select "one step back from the bleeding edge" components, and that has worked out well.

If you build a system with the latest and greatest hardware, make sure you use the latest and greatest operating system. If you try to install 16.04 on a motherboard from 2017, you're just asking for trouble.

---

### Post by mastablasta on 2017-02-10
> **robbie 348 said:**
>               
Thanks for the tip. I never knew you could mix Nvidia and AMD, Rob.

AMD and Intel CPUs both use the same x86 processor architecture. and CPU Works independently form GPU. in fact you do not need GPU if you plan to do CPU only tasks (this is for example i a headless web server [headless=no monitor attached] ). But the AMD and Intel CPUs have different sockets ,which is why they each need their own specific motherboard. their design is also different. bu thtey can boith run programs written and compiled for x86 architecture.

GPU is another thing. it runs graphics stuff mostly. fast graphics are important in games. which is why you can actually build a strong gaming rig with relatively weak CPU and powerfull GPU. mix and match the CPU and GPU depending on your needs. Games need to load and process large texturer which is why it is good to have dedicated RAM on the GPU for doing that rather than using disk. GPUs that ar eon the chip will use the PC RAM. this means info goes form disk through CPU to RAM and then to GPU to be processed and possibly back to ram... in any case it is not as efficient.

So yes, you can mix AMD CPU and nVidia GPU, or Intel CPU and AMD GPU. There are even laptops with dual graphics that have Intel CPU and Intel GPU (for Office stuff)+ dedicated AMD GPU (for games).

if oyu are tight on a budget and don't mind 15-20% slower CPU then AMD + nVidia sound good. but if you have the money then go for Intel. For GPU in Linux nVidia is still better supported, but AMD support is also improving very fast because it is opensource. new versions come out fast and improvements are added, bugs fixed. but you need to make sure the GPU is new and supported by latest drivers.

---

