---
title: "Reusing a old PC"
date: 2012-07-02
forum: Hardware
---

### Post by alkaza on 2012-07-02
Hi!, I've a old PC i'd like to use with ubuntu to make domestic task, play music, internet, text edit... but don't discard the possibility to use it like HTPC, so it have to be able to play videos at high resolution. The actual configuration is this:

-Unknown power supply
-CPU Intel Pentium D 3Ghz
-Motherboard Asus P5LD2
-GPU NVidia GeForce 6600 (it make too much noise)
-1GB Value RAM Kingston 
-HD 1TB

In principle i only wish change the GPU but, if I replace it by a new GPU it could make bottlenecking with de CPU (I'm not sure).
The other possibility is to change motherboard, CPU and GPU, but it cost more money that i'm arranged to spend. 

¿What do you think? ¿should i change all components? ¿only the GPU?

Thanks

---

### Post by kurt18947 on 2012-07-02
The only thing I'd change beyond the GPU is maybe add RAM.  1 GB will work, IMO 2 GB. is nice, 4 GB if you're considering virtual machines.  My (inexpert) understanding is that Linux will use RAM  no used for the OS as a disk cache, sorta like the hybrid disk drives.  I just installed an Nvidia 210 card in a dual core AMD machine.  It seemed like a nice value choice for a non-gamer machine.  I got it for $29 at a CompUSA store

[http://www.amazon.com/PNY-Geforce-PCIE-DDR3-Adapter-VCG2101D3XPB/dp/B0063E404Y/ref=sr_1_2?ie=UTF8&qid=1341232717&sr=8-2&keywords=pny+geforce+210](http://www.amazon.com/PNY-Geforce-PCIE-DDR3-Adapter-VCG2101D3XPB/dp/B0063E404Y/ref=sr_1_2?ie=UTF8&qid=1341232717&sr=8-2&keywords=pny+geforce+210)

---

### Post by Lars Noodén on 2012-07-02
+1 for adding RAM.  Having enough to avoid swapping will really improve performance.  Having 1 or 2 GB will be more than enough for that.

Other than that you might look at reducing the system load, one way would be to use a lighter weight desktop environment or even just a window manager by itself.  The lightest distro out of the box would be Lubuntu.

---

### Post by cortman on 2012-07-02
Old? That machine has great specs.
Put Lubuntu, Bodhi, Crunchbang, Slitaz, or some other lightweight distro on it and it'll fly.

---

### Post by alkaza on 2012-07-02
Thanks guys for help! 
Yep, you're right, RAM is very poor, I think I'll add 3/2 GB more. Can I add some DDR3 modules to this motherboard? It accepts DDR2 but I don't know if it can downgrade by itself DDR3 to DDR2. Anybody knows? 

A friend has recommended to me to buy this card:
[http://www.pccomponentes.com/sapphire_radeon_hd_6570_ultimate_1gb_gddr3.html](http://www.pccomponentes.com/sapphire_radeon_hd_6570_ultimate_1gb_gddr3.html)

It've passive refrigeration and seems to work fine.

---

### Post by oldfred on 2012-07-02
I cannot read specs but it looks like it wants a system with a 400 watt power supply. Sometimes they also specify so many amps on the main rail. I had a 400 watt power supply but it claimed 17 amps on the 12 volt rail, but had several 12v rails, but a card I was looking at wanted 18. It probably would have worked but I did not want to risk it. That was several years ago and power requirements for video cards have further increased. And I notice some power supplies now have high ratings all on one rail.

Either disassemble system to see specs on your power supply or get a lighter weight power supply. Many vendor systems only put in a power supply for the components specified. Usually not much room to upgrade, as they are trying to save cost.

---

### Post by ljonesj on 2012-07-02
you cannot put in ddr3 ram into a ddr2 mother board the key way aka the cut out on the memory sticks are in different postions

---

### Post by ahallubuntu on 2012-07-02
The Pentium D is a dual core CPU, but it's probably Intel's worst.  A Pentium D is basically two Pentium 4 chips in a single package, so it runs very hot and takes more power.  The Core 2 Duo that came just after is vastly superior technology: runs much cooler and faster.  People may think a Core 2 Duo is "slower" because the first chips ran at low clock rates, but the CPU architecture is completely different.  It is designed to run at a lower clock rate to achieve the same performance.  A 1.6GHZ Core 2 Duo would be roughly equivalent to a 3GHZ Pentium D but run much cooler than a Pentium D.

If the motherboard would accept it, I'd consider upgrading to at least a Pentium Dual Core (budget CPU which is based on Core 2 Duo, not related to old/hotter "Pentium D").  Depends on the price. Some of these CPUs can be had cheaply on eBay etc. A 2.2GHZ Pentium Dual Core would be faster than a Pentium D 3GHZ.  It would also reduce the load on the power supply, allowing you to upgrade other components perhaps without upgrading the power supply.

---

### Post by Yellow Pasque on 2012-07-02
Get yourself an nvidia gt430 or gt520. They're good HTPC cards.

The Asus P5LD2 accepts Core2-based CPUs. If you go that route, make sure BIOS is updated before pulling the old CPU.

---

### Post by alkaza on 2012-07-02
There's a problem with that, yes, my MB support Core 2 Duo, but only since PCB 2.01G, this one is Rev 1.03G I don't understand what this numbers means, if BIOS version is greater than the version showed in the web the C2D CPU will work? PCB and BIOS version need to be greater? :confused:
Here's the list of supported CPU.

I'm gonna try to see what BIOS version is running now.

---

### Post by Dlambert on 2012-07-02
My parents had the same build but the Mb failed. +2 to adding ram, as much as you can. The cpu is fine as is, it doesn't NEED to be updated, so I would update the GPU first. +1 to Nvidia.

---

### Post by Yellow Pasque on 2012-07-02
> **alkaza said:**
> There's a problem with that, yes, my MB support Core 2 Duo, but only since PCB 2.01G

Then your mobo does **not** support Core/2 Duo. (Sorry, I should have seen the warning on Asus' site.)

---

### Post by ahallubuntu on 2012-07-02
Yes, it sounds like you can't use a Core 2 Duo on that motherboard - bummer!

The Pentium D will work fine, just expect it to run a little hot and not be as fast as a newer CPU.

---

### Post by alkaza on 2012-07-03
Definitively, I gonna add more RAM, I think 3GB will be ok, the GPU Saphire Radeon HD 6570 Ultimate: 
[http://www.sapphiretech.com/presentation/product/?cid=1&gid=3&sgid=1087&pid=1241&psn=&lid=1&leg=0](http://www.sapphiretech.com/presentation/product/?cid=1&gid=3&sgid=1087&pid=1241&psn=&lid=1&leg=0)

The CPU change is nonviable or a little difficult so, I'll leave the pentium D where it is for a few years.
I was thinking to change the mobo and CPU by a AMD Athlon X3 it cost approximately 100$, but I wont make a intensive use by now, maybe in two years...

Thanks guys! :D

---

