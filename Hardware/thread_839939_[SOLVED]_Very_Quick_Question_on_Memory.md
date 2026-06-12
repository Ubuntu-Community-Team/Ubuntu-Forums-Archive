---
title: "[SOLVED] Very Quick Question on Memory"
date: 2008-06-24
forum: Hardware
---

### Post by gali98 on 2008-06-24
I am buying 4 gigs of memory for my new lappy (tx2000z) and am wondering a few things about memory.
The Laptop takes DDR2 667 (PC2 5300) laptop memory.
If I was to use DDR2 667 (PC2 5400) would that work as well as the other? There is a great deal on Newegg for the latter that does not exist for the former.

My next question is about 32/64 bit. I know on Vista that you can only get 3.3~ gigs of usage on a 32 bit and need to go to 64bit to use all 4 gigs.
Is this also a problem on linux? I am assuming it is, but you never know on linux...
Thanks,
Kory

---

### Post by tamoneya on 2008-06-24
First of all the laptop will just run the memory as if it is PC2 5300.  It never hurts to buy faster memory (provided the CL isnt lower) the only thing you could be losing is money. 

As for the 3.3 GB problem the same issue exists in linux.  I run the 64 bit edition and 4 GB of ram.  Runs no problem.

---

### Post by wdaniels on 2008-06-24
> **gali98 said:**
> I am buying 4 gigs of memory for my new lappy (tx2000z) and am wondering a few things about memory.
The Laptop takes DDR2 667 (PC2 5300) laptop memory.
If I was to use DDR2 667 (PC2 5400) would that work as well as the other? There is a great deal on Newegg for the latter that does not exist for the former.

This only has to do with which way the manufacturer decides to round the numbers, there is no difference.

> **gali98 said:**
> My next question is about 32/64 bit. I know on Vista that you can only get 3.3~ gigs of usage on a 32 bit and need to go to 64bit to use all 4 gigs.
Is this also a problem on linux? I am assuming it is, but you never know on linux...

If you want to have a single process address more than 4GB of memory then you need 64-bit, but since that's very unlikely to be the case, you could potentially just use the server version of the 32-bit Ubuntu kernel which has PAE enabled to let you use the extra memory. But there is a minor performance hit for using PAE as opposed to a minor performance gain using 64-bit, so I would suggest the latter in most cases.

---

### Post by gali98 on 2008-06-25
Thanks guys! You confirmed my thoughts. I will probably buy the cheaper ram (which happens to be 5400) and will continue to use 32 bit for now. I don't want the hastle of having to mess with 64 bit right now. I'm fine with not using less than a gig of memory... It's only 70-something bucks.
Thanks, Marked as Solved!
Kory

---

### Post by wdaniels on 2008-06-25
OK, but 64-bit Linux is not very much trouble at all really.

As for PAE, one of the things with Linux is that you don't have to choose just one particular kernel. You can always just:

```
sudo apt-get install linux-image-server
```

...and then you should have the option to boot using the server kernel to get the full 4GB RAM. Just an idea...

---

### Post by gali98 on 2008-06-28
So basically this PAE thing compiled into the server kernel that lets 32-bit use 4 Gigs? Sound interesting, and I might check it out. I am actually thinking of installing 64-bit ubuntu into another partion now anyway, so I might do both. Thanks!
Kory

---

### Post by wdaniels on 2008-06-28
> **gali98 said:**
> So basically this PAE thing compiled into the server kernel that lets 32-bit use 4 Gigs?

Yes, what happens with PAE (Physical Address Extension) is that each program still uses a 32-bit address space (so each individual process can only address up to 4GB) but this can be mapped into a range somewhere within up to 64GB of installed memory.

PAE is chiefly a feature of the processor, but the OS does need to actually use the extension. The Linux kernel has had full PAE support since 2.6 but if I understand things correctly, it has to be compiled either to use PAE or not to, and compiling the desktop kernel with PAE support would break systems with old CPUs that don't support it. It is enabled in the default server kernel because it is a more reasonable assumption that a server will have a PAE-enabled processor and because it is likely that a server will have more than 4GB of RAM these days.

Note that your BIOS will also need to support 4GB of memory, though normally you can update it if it doesn't.

For reference, you can check whether your CPU has PAE support using:

```
cat /proc/cpuinfo
```

and look for "pae" in the "flags" line, but in this specific case that's not necessary since you seem to have a 64-bit CPU, which will definitely have it.

Some versions of Windows can also use PAE but you have to buy the most expensive server varieties to get the full 64GB support.

---

