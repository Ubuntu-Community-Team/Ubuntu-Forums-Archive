---
title: "Opinions for a new system I may build?"
date: 2012-01-28
forum: Hardware
---

### Post by mfdc1969 on 2012-01-28
SO my Athlon XP 4000+ single core and related hardware just ain't cutting it anymore ... I am planning to build a new box and have pieced together some ideas for hardware and would like opinions on it:

[INDENT]Antec PS EA-750 GreenATX12V v2.3
[http://www.antec.com/Believe_it/product.php?id=NzA0NDE1](http://www.antec.com/Believe_it/product.php?id=NzA0NDE1)

Antec Nine Hundred Two Case								
[http://www.antec.com/Believe_it/product.php?id=NzIyJjI=](http://www.antec.com/Believe_it/product.php?id=NzIyJjI=)

Crosshair V Formula								
[http://ca.asus.com/en/Motherboards/AMD_AM3Plus/Crosshair_V_Formula/](http://ca.asus.com/en/Motherboards/AMD_AM3Plus/Crosshair_V_Formula/)

AMD Bulldozer FX-8120 8 Core Processor 3.1GHZ Socket AM3+ 125W
[http://www.amd.com/us/products/desktop/processors/amdfx/Pages/amdfx-model-number-comparison.aspx](http://www.amd.com/us/products/desktop/processors/amdfx/Pages/amdfx-model-number-comparison.aspx)

2x Seagate Barracuda 2TB 7200RPM SATA3 64MB Cache 3.5IN HDD		

RAM
8GB of DDR3-2000/2133/2200/2300 depending on availability and compatibility

ASUS Radeon HD 6870 (EAH6870 DC/2DI2S/1GD5)
DirectCU 913MHZ 1GB 4.2GHZ GDDR5 2XDVI 2XMINI DisplayPort HDMI PCI-E Video Card
[http://ca.asus.com/en/Graphics_Cards/AMD_Series/EAH6870_DC2DI2S1GD5/](http://ca.asus.com/en/Graphics_Cards/AMD_Series/EAH6870_DC2DI2S1GD5/)

Samsung SH-B123L 12X BD-ROM & DVD Burner Combo Internal SATA
SH-B123L/RSBP

Internal Multi-format card/flash memory reader

No sound card selected as I hope to use the on-board sound.[/INDENT]

My primary use for this will be minor video editing (HD/AVCHD), photoshop, a bit of office type stuff and I may eventually go with a dual monitor setup ...

---

### Post by 2F4U on 2012-01-29
The AMD Bulldozer is still very new and I've seen posts on this forum where people report problems with the current kernel. These are probably resolved with the next kernel 3.2 version. Just wanted to let you know.

---

### Post by mfdc1969 on 2012-01-29
Yes, I have read hints of that on other websites about the FX-8150, but does that also relate to the other new FX CPUs like FX-4100,6100, 8100 etc.

My theory is to invest some money upfront, more than I normally would, and buy big to start in the hopes I can survive a few more years as technology changes. My current desktop has troubles and I don't want to sink money into upgrades when technology is changing so rapidly. I'm not needing latest greatest but I thought perhaps by investing in the newest technology I might get a few more years of usability down the road.

Any opinions out there about whether or not I should:

A) choose AMD  
B) go with an Intel i5/i7 build

Thanks for the feedback!

---

### Post by andrew.46 on 2012-03-05
> **2F4U said:**
> The AMD Bulldozer is still very new and I've seen posts on this forum where people report problems with the current kernel. These are probably resolved with the next kernel 3.2 version. 

No problem with FX-8150 here:

```

andrew@skamandros~$ uname -a
Linux skamandros 3.2.7 #1 SMP Fri Feb 24 16:39:45 CST 2012 x86_64 AMD FX(tm)-8150 Eight-Core Processor AuthenticAMD GNU/Linux

```

But I am running the newer kernel.....

---

### Post by SlasherIT on 2012-03-05
Go with an Intel i7-2600k or i5-2500k depending on your resources, its better than Bulldozer. But honestly, if you are going the Intel route, I'd wait a bit for Ivy Bridge to come out.

---

### Post by andrew.46 on 2012-03-05
> **SlasherIT said:**
> Go with an Intel i7-2600k or i5-2500k depending on your resources, its better than Bulldozer.

I think the issue is actually not that clear, read [the summary here]("http://www.phoronix.com/scan.php?page=article&item=amd_fx8150_bulldozer&num=13") of some benchmarking tests.

---

### Post by idoitprone on 2012-03-05
> **andrew.46 said:**
> I think the issue is actually not that clear, read [the summary here]("http://www.phoronix.com/scan.php?page=article&item=amd_fx8150_bulldozer&num=13") of some benchmarking tests.
 
actually the issue is very clear. Bulldozer implements their version of hyperthreading, which make some major speed improvements. Unfortnately, they are at the mercy of an Intel world, so most software are unable to use those speed improvements of Bullzoder. Heck, Window's scheduler is not optimized for bullzdozer too. Bullzoder have advantages in integer arithmetic but loses all it benefits for floating point numbers. To get the true performance which is pretty close to a i5, you have to compile against the architecture, unfornately, it means using Gentoo as your main distro, and binary blobs will not receive any benefit.
 
It easier to get intel 2500k or the next gen 3500k, then to deal with bulldozer

---

### Post by andrew.46 on 2012-03-05
> **idoitprone said:**
> Bulldozer implements their version of hyperthreading, which make some major speed improvements. Unfortnately, they are at the mercy of an Intel world, so most software are unable to use those speed improvements of Bullzoder. Heck, Window's scheduler is not optimized for bullzdozer too. Bullzoder have advantages in integer arithmetic but loses all it benefits for floating point numbers. To get the true performance which is pretty close to a i5, you have to compile against the architecture, unfornately, it means using Gentoo as your main distro, and binary blobs will not receive any benefit.

You have made some excellent points and perhaps I have been blinded a little by my own computing practice which is to use the development version of slackware as my base distro with Ubuntu vms. I also compile and run my own transcoding software (x264, FFmpeg and friends) plus compile my own kernels, thus I expect to receive all the present and possible future benefits of the Bulldozer chips as you have described.

It will be an interesting path for early adopters such as myself and perhaps the *safest* course would be an intel chip for a new build but then it might also be safer to stick with windows :).

---

### Post by idoitprone on 2012-03-05
> **andrew.46 said:**
> You have made some excellent points and perhaps I have been blinded a little by my own computing practice which is to use the development version of slackware as my base distro with Ubuntu vms. I also compile and run my own transcoding software (x264, FFmpeg and friends) plus compile my own kernels, thus I expect to receive all the present and possible future benefits of the Bulldozer chips as you have described.

It will be an interesting path for early adopters such as myself and perhaps the *safest* course would be an intel chip for a new build but then it might also be safer to stick with windows :).

[http://en.gentoo-wiki.com/wiki/Safe_Cflags/AMD#AMD_FX-8xxx.2F6xxx.2F4xxx_.28Bulldozer.29](http://en.gentoo-wiki.com/wiki/Safe_Cflags/AMD#AMD_FX-8xxx.2F6xxx.2F4xxx_.28Bulldozer.29) 

so you compiled with these flags? If you didnt then you wasted your time. This is why going for i5 2500k is easier

---

### Post by alegomaster on 2012-03-05
I am personally waiting for the ivy bridge 3770k (top line i7 model; I may got the model number wrong) to come out so that I can build my Linux Compile crusher computer.

---

### Post by idoitprone on 2012-03-05
> **alegomaster said:**
> I am personally waiting for the ivy bridge 3770k (top line i7 model; I may got the model number wrong) to come out so that I can build my Linux Compile crusher computer.

unfornuately for you intel relase their benchmarks and it is clear that they dont really care about cpu performance. they just upped the graphic performance which does not matter if you use a desecrate graphic card. This is great for laptops thou

[http://www.tomshardware.com/news/Benchmarks-Intel-Ivy-Bridge-CPU-sandy-bridge,14144.html](http://www.tomshardware.com/news/Benchmarks-Intel-Ivy-Bridge-CPU-sandy-bridge,14144.html)

---

### Post by andrew.46 on 2012-03-05
> **idoitprone said:**
> [http://en.gentoo-wiki.com/wiki/Safe_Cflags/AMD#AMD_FX-8xxx.2F6xxx.2F4xxx_.28Bulldozer.29](http://en.gentoo-wiki.com/wiki/Safe_Cflags/AMD#AMD_FX-8xxx.2F6xxx.2F4xxx_.28Bulldozer.29) 

so you compiled with these flags? 

I do now :).

---

### Post by alegomaster on 2012-03-05
> **idoitprone said:**
> unfornuately for you intel relase their benchmarks and it is clear that they dont really care about cpu performance. they just upped the graphic performance which does not matter if you use a desecrate graphic card. This is great for laptops thou

[http://www.tomshardware.com/news/Benchmarks-Intel-Ivy-Bridge-CPU-sandy-bridge,14144.html](http://www.tomshardware.com/news/Benchmarks-Intel-Ivy-Bridge-CPU-sandy-bridge,14144.html)

Luckily for me Intel decided to make their ivy bridge cpus with a 22 nm 3d transistor tech, which means that I will have a lower tdp, so there is a better chance of me hitting 5ghz. Also I think it comes with some new math extension too.

---

### Post by fjgaude on 2012-03-05
Well, 15-20% greater quickness for the same clock speed, that's not bad, and doing it for less power. I'll be likely buying an Ivy Bridge CPU for my 1155 motherboard, when they come out, soon!

---

### Post by andrew.46 on 2012-03-14
Links are gone for motherboard but I assume the board + front case connections run usb 3.0? For my recent build I ensured this was the case and I have found usb 3.0 amazing, more and more devices will support this in the coming months / years.

---

