---
title: "Installing New RAM (memory)"
date: 2013-03-29
forum: Hardware
---

### Post by pwert00 on 2013-03-29
Hi all,

I recently purchased some new RAM for my computer from Staples, at the same time as I purchased the new computer that I bought.  At Staples they assured me that the RAM was compatible with my computer.  However, after installing the RAM myself I have found that my computer is not recognizing that there is any RAM.  I was wondering if anyone could help me.  

I already had 4GB of RAM installed, and I installed another 4GB of RAM.  I am using Ubuntu x64 so it will recognize more RAM, and I checked in my BIOS to make sure.  Only 4GB is showing up.  The RAM is pushed in "all the way", and I know that my RAM port is working.  

My computer is a HP Pavilion g6-2235.  The RAM that I purchased has the information below.  I am somewhat of a beginner and do not know what all of the data below is for, but if you can make sense of it then let me know.  

L/4G-DDR3-1066 SODIM
4GB PC8500 DDR3 1066 MHZ
9857462

I read online doing BIOS updates maybe, but I don't know how to do a BIOS update (or how it would be useful).  Let me know if any of you can help me!

Thanks

---

### Post by pfeiffep on 2013-03-29
I think you need to go back to Staples, a quick check about the RAM on line indicates that it should be compatible
 > [TABLE="width: 100%"]
[TR]
[TD]Laptop Memory Type[/TD]
[TD]DDR3 SDRAM (1 DIMM)

[/TD]
[/TR]
[/TABLE]


---

### Post by andrew.46 on 2013-03-29
The motherboard will usually have a preferred order that RAM should be installed. For example if there are 4 banks available for RAM you might have to use banks 1 and 3 rather than 1 and 2, or some permutation of this. Your motherboard manual should have the details, hopefully it is something this simple :).

---

### Post by pwert00 on 2013-03-29
I have only two memory banks.  I tried switching the spots that the RAM is in, but it didn't help :(

---

### Post by andrew.46 on 2013-03-29
Then I am not sure I'm afraid :(. Perhaps run *uname -m* just to triple check you have 64bit system but more than likely you will have to take RAM *and* computer back to the store.

---

### Post by sanderj on 2013-03-30
> **pwert00 said:**
> I have only two memory banks.  I tried switching the spots that the RAM is in, but it didn't help :(

... and each SODIMM is 4GB? What happens if you have only one SODIMM in your laptop? 4GB, for each of both SODIMMs?

EDIT: 

Hypothese 1: only one 4GB-SODIMM is working at all
Hypothese 2: your hardware can only handle 4GB max ...

/EDIT

Have you been been to find a specification about the max memory your laptop can handle?

---

