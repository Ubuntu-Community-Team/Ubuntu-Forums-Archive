---
title: "4GB RAM Limit"
date: 2009-08-19
forum: Hardware
---

### Post by Nate Shoffner on 2009-08-19
I am just wondering if, when you have 4GB of RAM installed on your computer and the limit for 32-bit is about 3GB, does that mean it only shows up as 3GB but still uses that extra GB of memory or what?  Sorry if this sounds kind of stupid.

---

### Post by Revolutionary101 on 2009-08-19
> **Nate Shoffner said:**
> I am just wondering if, when you have 4GB of RAM installed on your computer and the limit for 32-bit is about 3GB, does that mean it only shows up as 3GB but still uses that extra GB of memory or what?  Sorry if this sounds kind of stupid.

32 bit computers can address 4 GB. It will show and use all of the 4 GB of RAM. The 3 GB limit is just something Windows has.

---

### Post by Nate Shoffner on 2009-08-19
Well I currently have 4GB of RAM installed.  BIOS detects 4GB, but Ubuntu only detects 3.3GB. :confused:

---

### Post by Revolutionary101 on 2009-08-19
> **Nate Shoffner said:**
> Well I currently have 4GB of RAM installed.  BIOS detects 4GB, but Ubuntu only detects 3.3GB. :confused:
That is weird because I did the math and 32 bit computers can support up to 4 GB. Here is the math.

2(this is the 0 and 1)^32(bits of address space)/1024(converts it to kilobytes)/1024(coverts to megabytes)/1024(converts to gigabytes)= 4 GB

I also compiled my own Linux kernel and it said that the Linux kernel supports up to 4 GB of RAM on 32 bit systems. Maybe it has something to do with your BIOS, even though it may show 4 GB of RAM it may only allow the computer to use 3.3 GB.

---

### Post by Nate Shoffner on 2009-08-19
Hmm...any way I can possibly figure out how much my computer allows?  

I ran free -m and these were the results:

```

             total       used       free     shared    buffers     cached
Mem:          3402       1308       2093          0         47        757
-/+ buffers/cache:        503       2898
Swap:          478          0        478

```

---

### Post by DownTown22 on 2009-08-19
Nope...as far as I know, you're only going to be able to use 3.3GB of that 4GB.

---

### Post by Revolutionary101 on 2009-08-19
I think you are going to have to check your computer manufacter's manual. If you built your own computer search for your motherboard model online and look for it's limit.

---

### Post by Revolutionary101 on 2009-08-19
> **DownTown22 said:**
> Nope...as far as I know, you're only going to be able to use 3.3GB of that 4GB.

Then explain this:
[http://www.spack.org/wiki/LinuxRamLimits](http://www.spack.org/wiki/LinuxRamLimits)

---

### Post by Yellow Pasque on 2009-08-19
The BIOS will reserve some of the address space for hardware, so 3.4GB sounds right.

Possible ways around this:
1) Use 64-bit OS and enable memory-remapping in your BIOS if it supports it
2) Use a kernel with PAE
3) Monitor your RAM usage and see if you can actually use 3.4GB of RAM under your normal workload before you get concerned with addressing more :)

---

### Post by Nate Shoffner on 2009-08-19
> **Temüjin said:**
> The BIOS will reserve some of the address space for hardware, so 3.4GB sounds right.

Possible ways around this:
1) Use 64-bit OS and enable memory-remapping in your BIOS if it supports it
2) Use a kernel with PAE
3) Monitor your RAM usage and see if you can actually use 3.4GB of RAM under your normal workload before you get concerned with addressing more :)

It's not that I necessarily need it.  I was just curious because I Know Windows will not read all 4GB of RAM, but I wasn't completely sure about Linux.  I haven't really looked into 64-bit but from what I've heard, is that some applications aren't fully compatible with it.  Now, if I did what you said and used a kernel with PAE, will that impact anything else on the system in a negative way?

---

