---
title: "Modern processors are 32-bit?!!"
date: 2009-11-04
forum: Hardware
---

### Post by fifoKamb3 on 2009-11-04
Hello,
I think I am seriuosly misleaded by a book I was reading about CPU's:
> 
Pentium --- 60/66 MHz --- 3,1 million transistors (.8 micron) --- **64 bits**/32 bits --- 4 GB addressable memory
...
...
Celeron --- 266/300 MHz --- 7,5 M t (.25 micron) --- **64 bits** --- 4 GB
..
...
....
Pentium 4 HT --- 3,40/3,60 GHz --- 90 nanometer -- **64 bits** --- **64 GB**
If even Celeron 266 MHz (let's say maybe also Pentium 66 MHz) was 64-bit, then there has to be no doubt that all other more modern processor are 64-bit? 

[http://en.wikipedia.org/wiki/64-bit#64-bit_processor_timeline](http://en.wikipedia.org/wiki/64-bit#64-bit_processor_timeline)

I don't understand this well.
Thanks, br.

---

### Post by P4man on 2009-11-04
Define what you call a "64 bits" cpu.
It can refer to many things, from memory bus width to register size to address bus width. These are all VERY different things.

Your list lists addressable memory, so Im guessing that its what you are interested in? There is no cpu on the market today that can physically address 64 bits of memory. Modern cpu's use 64 bit addressing (so software uses 64 bits to address a memory location) but only connect enough pins to the motherboard to allow anywhere from 36 to  48 bits wide **physical** address path. The reason is simple, the pile of RAM modules needed to max out 64 bit wide addressing would be higher than the empire state building. In fact IIRC it would reach the international space station without exaggerating. 

Register size is a more common way to differentiate cpu's. A cpu with 64 bit wide registers can do math with 64bit wide variables, and since these can contain memory addresses, then  can address 64 bit (**virtual**) memory spaces. The first common CPU that allowed this was the AMD Athlon 64 and Opteron. The last Pentium 4s could do this too and every cpu released after that can do it. Those are called "64 bit" and can use 64 bit software, like 64 bit ubuntu. A 233 Mhz celeron or pentium pro can **not**. Those are 32 bit cpu's, although some have them had larger than 32 bit wide address busses meaning they could address more than 4GB physical RAM. How is that possible with narrow 32 bit wide registers? Through PAE (google on it). An ugly hack.

The last bit thing Ill mention here is frontside bus width  as i suspect thats what actually listed in your.. list. That just determines how many bits per clock the cpu can send over the frontside bus to the ram or back (if it uses one). It has an impact on performance to some extent but you can safely ignore that value for just about anything. It got famous with the old 386 chip, the first ones had a 32 bit memory bus, later they created a slower 386SX verson with a 16 bit memory bus. People wrongly thought that meant it wasnt a "real" 32 chip. It sure was, just a bit slower.

---

### Post by P4man on 2009-11-04
One more thing. 64 bit chips, as in, 64bit wide registers, can also run 32 bit software without problem. But you are then limited to a 4GB virtual address space, like 32 bit cpus.

---

### Post by cascade9 on 2009-11-04
100% correct, and (I think) what fifoKamb3 means is the data bus width. Well, one minor error. 

> **P4man said:**
>  The first common CPU that allowed this was the AMD Athlon 64 and Opteron. The last Pentium 4s could do this too and every cpu released after that can do it. 

The original Intel 'Core' CPUs, the Core Duo and Core Solo, were 32bit only. 

[http://en.wikipedia.org/wiki/Intel_Core](http://en.wikipedia.org/wiki/Intel_Core)

It wasnt till the Core 2 Duos/Solos that the Core CPUs went 64bit.

---

### Post by P4man on 2009-11-04
> **cascade9 said:**
> 

It wasnt till the Core 2 Duos/Solos that the Core CPUs went 64bit.

Agreed. But those where just rebranded Pentium Ms which were released before the 64 bit enabled P4s if I remember right. i guess you could also find some Athlon XPs, mobile K7s and some VIA chips and what not all  released after the K8, but I was generalising :)

---

### Post by cascade9 on 2009-11-04
Fair point. The Core Duo/Solo were a little bit more than a rebranded P-M, but near enough.

There probably were Athlon XPs released after the K8s, but there wasnt any new silicon coming out, just better made/higher clock speed versions. (which is why I pointed out the 1st Cores, they were new silicon).  I think. I could well be wrong, theres a lot of oddball CPUs around.

---

### Post by fifoKamb3 on 2009-11-05
Thanks, maybe the author refers to different things. In the same book he says: **It is AMD with Athlon 64 that introduced the first "[COLOR="Red"]valuable[/COLOR]" (??) 64-bit processor in the market**.

Pentium 60/66 MHz ...... 46 bits/32 bits (bus width) 
Pentium 75/90/100 MHz .. 46 bits/32 bits (bus width)

ubuntu-9.10-server-amd[COLOR="DarkGreen"]**64**[/COLOR]
Is this 64 here meaning the _bush width_?

---

### Post by P4man on 2009-11-05
> **fifoKamb3 said:**
> Thanks, maybe the author refers to different things. In the same book he says: **It is AMD with Athlon 64 that introduced the first "[COLOR="Red"]valuable[/COLOR]" (??) 64-bit processor in the market**.

Pentium 60/66 MHz ...... 46 bits/32 bits (bus width) 
Pentium 75/90/100 MHz .. 46 bits/32 bits (bus width)

ubuntu-9.10-server-amd[COLOR="DarkGreen"]**64**[/COLOR]
Is this 64 here meaning the _bush width_?

No. That refers to register width. The most common use of the term "64 bit". . You need an AMD64  compatible cpu to run that, which is all the cpu's listed above (basically all AMD cpu's since the A64 and (allmost) all intel cpu's since the last generation of Pentium 4s). A pentium 60  or 100 is utterly unable to run AMD64 code.

---

