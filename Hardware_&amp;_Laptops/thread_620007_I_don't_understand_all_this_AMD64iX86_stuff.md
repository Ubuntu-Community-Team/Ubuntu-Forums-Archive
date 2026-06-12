---
title: "I don't understand all this AMD64/iX86/ stuff"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by fidelisprivatus on 2007-11-22
Is there an easy explanation on what all these processor architectures mean?  When I see AMD64/x86/i386/i486/i586/i686/etc. I have no idea what I'm really looking at.

I think I somewhat understand the 32bit vs 64bit thing, where a 32bit OS will not install on a 64bit processor but the other way around it will work.

Do certain versions of OS's only work on certain processors (AMD vs Intel)?  Why are there so many different architectures?  What will work on what?  If I have a computer with an Intel processor but I have the AMD64 version of Ubuntu will it work on my processor?

---

### Post by linuxonbute on 2007-11-22
> **fidelisprivatus said:**
> Is there an easy explanation on what all these processor architectures mean?  When I see AMD64/x86/i386/i486/i586/i686/etc. I have no idea what I'm really looking at.



Well I cannot answer all your questions completely but can perhaps give you some idea

---------> IN SIMPLE TERMS. <---------

The  AMD64/x86/i386/i486/i586/i686/ is quite easy
Think about anything which has been made eg washing machines
First ones could do very little perhaps just heat the water and stir the washing.
Later ones might have a spin drier and so on
Also one manufacturer might have a top opening machine but another front opening.
It's similar with cars, radios - well most things really.

Before any of these tere were 4Bit and 8Bit machines.
8Bit really took off. 2 Processors were very popular
The Z80 (made by a company called Zilog ) was used in the Sinclair Zx80, Zx81, Spectrum, Tandy TRS80 and others.
The 6502 was used in Commodore Petand others too.
These were not in the same class as the ones you mean.

For processors today there are mainly only Intel and AMD making them ( Yes- I know there are others)
Both are in competition and have made variations of most architectures.

Of those you mention, the order of power and complexity and the time line are
386,486,586,686 then names came into play. 
Can't remember the exact order but names like Celeron, Pentium, Duron, Athlon are among them
Early processors in the range were 16Bit, then came 32Bit and now 64Bit.

> 
I think I somewhat understand the 32bit vs 64bit thing, where a 32bit OS will not install on a 64bit processor but the other way around it will work.

This is the other way round 32Bit will install on a 64Bit
> 

Do certain versions of OS's only work on certain processors (AMD vs Intel)? Why are there so many different architectures? What will work on what? If I have a computer with an Intel processor but I have the AMD64 version of Ubuntu will it work on my processor?

A 16Bit OS will run on 16Bit/32Bit/64Bit Processors.
A 32Bit OS will run on 32Bit/64Bit Processors.
A 64Bit OS will run on 64Bit Processors.

Currently, as far as I know, all 32Bit will run on either but I don't know about the 64Bit. However I expect they would have to work in a similar way even if they are different internally.

You will find that as each architecture comes out with it's advantages, older ones will soon become unavailable. Unless you find an ancient scrap unit you probably will only be able to buy fairly new types.

---

### Post by fidelisprivatus on 2007-11-22
Forgetting about the 32/64 bit processors...

Is there a difference between AMD64 and i486?  I ask because looking around at different distros, some say you can download the AMD64 version and other sites say you can download the x86/i386/etc. version of the distro.  Will everything pretty much work on any Intel or AMD processor assuming it's the correct amount of bits?

Is x86 just a simple way to say i386/i486/i586/etc? Or are they completely different?

---

### Post by gobbles414 on 2007-11-22
fidelisprivatus,

Unfortunately, we cannot forget about the 32/64-bit stuff. With rare exceptions, i686 and below are considered to be 32-bit processors. AMD has also manufactured 32-bit Intel clones. So the letters AMD do not automatically mean 64-bit. EDIT: x86 by itself usually means 32-bit (i386-i686). x86-64 or similar means a 64-bit processor (usually Intel or AMD).

The AMD64 name is sort of weird because in software terms, it means an AMD **_or_** Intel processor that is 64-bit. So for example, AMD Turion 64 X2 and Intel Core _2_ Duo are both capable of running software labeled as AMD64. The reason for all of the naming confusion is that AMD came out with consumer 64-bit processors well before Intel did. All 64-bit Intel chips borrow heavily from AMD64 designs.

**32-bit processors CANNOT run 64-bit software. But 64-bit processors can run EITHER 32-bit or 64-bit software.**

I hate to confuse you even more, but a 64-bit processor does not always equal a fully 64-bit system. To save money, manufactures have been installing 64-bit processors on old 32-bit motherboards. This can really slow system performance, and has other negative consequences for users as well. **Intel calls there fully 64-bit systems Santa Rosa.** I honestly don't know how AMD designates their fully 64-bit systems. But a good way to determine whether a computer is fully 64-bit or not is by the amount of RAM it is able to use.

If it can use 4GB of RAM than it should be fully 64-bit. WARNING: some system descriptions falsely report the ability to support 4GB of RAM. Contact the manufacturer of the computer and be prepared to give the model number of the computer for more detailed information.

**When in doubt, install the 32-bit version of Ubuntu.**

---

### Post by eldragon on 2007-11-22
its AMD64 because amd created the x86 backwards compatible 64bit extensions to the x86 architecture, then they made a cross license agreement with intel.

they got to use sse2 and below, and intel got to use the amd64 instructions.

you have to worry about 3 types of instruction sets.

intels ia64 (itarium procesors) they were conceived as 64bit only processors, not backwards compatible with the x86 instruction set.

amd64 wich is a 64bit instruction set, you can run these procesors in 32bit x86 or 64bit x86 mode natively, its also pretty easy to make 32bit apps run on 64bit linux oses.

then i686 / i586 /  i386  are all 32bit instruction sets . they run no all newer procesors (ecept for ia64, which shouldnt worry you). they come with different optimizations each. all athlon 64 / intel pentium4 and beyond run these, not sure about athlonxp.

if unsure. use i386 :D

---

### Post by linuxonbute on 2007-11-22
> **fidelisprivatus said:**
> Forgetting about the 32/64 bit processors...

Is there a difference between AMD64 and i486? 


 Well yes - a vast difference.
an  i486 was 16Bit from the 1980's. Could only be used on motherboards which, if memory serves, could only handle hard discs of 32Megabytes ( NOT Gigabytes ) and a few Megabytes of memory.
AMD64 is 64Bit and pretty modern


> 
 I ask because looking around at different distros, some say you can download the AMD64 version and other sites say you can download the x86/i386/etc. version of the distro. 

Yes you can download the different ones but as I said 64Bit will only run on 64Bit computers Not on the 16/32 Bit ones.

> 
 Will everything pretty much work on any Intel or AMD processor assuming it's the correct amount of bits?

See above and my last post.
> 
Is x86 just a simple way to say i386/i486/i586/etc? Or are they completely different?


Again you need to understand that  x86 is the  architecture of the original IBM computer. 

It started with the 8086 processor then the 80286 followed by the 80386 and 80486

It's from these last 2 we get the terms i386 and i486. They are ANCIENT it computer terms but 

the terms are still used loosely.

As I understand it some distributions use kernels which CAN run on these but most are optimised 

to run on newer classes of processor and, for this reason will not work with them.

---

### Post by linuxonbute on 2007-11-22
If you want to learn more about optimization then a google search for processor architecture reveals sites such as 

[http://publib.boulder.ibm.com/infocenter/lnxpcomp/v9v111/index.jsp?topic=/com.ibm.xlf111.linux.doc/xlfopg/tuneforarch.htm](http://publib.boulder.ibm.com/infocenter/lnxpcomp/v9v111/index.jsp?topic=/com.ibm.xlf111.linux.doc/xlfopg/tuneforarch.htm)

and

[http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/dual-core-processor-optimization-441328/](http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/dual-core-processor-optimization-441328/)


If you are looking to install Linux on a PC you already have then why not tell us what it is.
One of us will be able to tell you what choices you have available for it.

---

### Post by Tweenk on 2007-11-22
linuxonbute, the part about max 4 GB of memory on 64-bit systems is wrong.
1. i386 is a designation for any system compatible with Intel's original 80386 processor, known as "386" for short. This a 32-bit processor which supports a flat 32-bit momery model, which means that it can access up to 4 GB of memory. Processors compatible with the 386 include: 486, Pentium, Pentium II, Pentium III, Pentium 4, Pentium M, Pentium D, Celeron, Xeon, K6, K7, Athlon, Duron, Opteron... nearly every desktop processor you can get today, except PowerPC processors found in Macs.
2. i486 is, likewise, anything compatible with the original 80486. Everything except PowerPC Macs and truly ancient computers is compatible.
3. i586 is a designation for anything compatible with a Pentium - ditto above
4. i686 is anything compatible with a Pentium Pro - ditto above
5. x86 is a broader term encompassing everything: 8086, 80286, 80386, 80486, Pentium, Pentium II, Pentium III, ... etc. without specifying the generation. This is important, because each new generation supported new instructions which weren't available in the previous one. This means that some code written for the new generations can't run on older generations (but not all). Because of this, most programs are compiled to use only the 386 instruction set, which is most limited, but supported on practically all x86 processors in existence.

**For practical purposes, x86 = i386 = i486 = i586 = i686**

6. AMD64 is a designation for a 64-bit extension of the x86 architecture. AMD64 systems can potentially access up to 2^64 B = **16777216 terabytes** (or 16384 petabytes, or 16 exabytes)  of memory. However, currently only 40 bits of the address are used, which allows for a maximum of 1 TB of memory (of which 512 GB is available to the user applications and 512 GB to the system). Currently no combination of motherboards and memory modules can provde such an amount of memory to a single processor.

**AMD64 processors are also manufactured by Intel** - for example all Intel Core 2 chips are AMD64. Intel's name for AMD64 is EM64T or Intel 64. Generic name is x86-64. x64 is a Microsoft term for the architecture.

**For practical purposes, x86-64 = AMD64 = EM64T = Intel 64 = x64**

---

### Post by linuxonbute on 2007-11-22
> **Tweenk said:**
> linuxonbute, the part about max 4 GB of memory on 64-bit systems is wrong.


I think that comment was from someone else.

All I can see that I said was 
> 
an i486 was 16Bit from the 1980's. 
Could only be used on >>>>>motherboards<<<<<<< which, if memory serves, could only handle hard discs of 32Megabytes ( NOT Gigabytes ) and a few Megabytes of memory.


And my last post suggested he tell us if he actually wants to install Linux on his system.

---

### Post by Tweenk on 2007-11-22
:shock: Of course I meant gobbles414. I guess it's too late for me to be able to read anything. :)

---

### Post by gobbles414 on 2007-11-22
Tweenk,

**You're speaking in theoretical terms. I'm speaking in reality!** Go check out the fine print on the [Dell Inspiron 1420N]("http://www.dell.com/ubuntu") (Dell's only Ubuntu laptop at the moment). The fine print states that **"Systems configured with 4GB memory or more: The total amount of available memory will be less than 4GB. The amount less depends on the actual system configuration."** This is because other items on the motherboard require the same resources as the RAM. Some computers lose MORE THAN 1GB of RAM to this. Indeed, early versions of the Intel-based Macs were only sold with 3GB of RAM maximum. Apple didn't want its customers paying the high premium for 1GB or more of useless RAM!

I must admit to my own ignorance regarding AMD's answer to this issue. But I know for a fact that Intel has fixed this problem thanks to Santa Rosa. However, lots of vendors are still selling hardware with older motherboards. In a few years, I think that 64-bit will have taken over completely. But until then, the consumer MUST be educated in order to purchase a true 64-bit system.

---

### Post by fidelisprivatus on 2007-11-23
Thanks for the help everyone.  This information was far better than other sites I tried reading about this on.

Oh and just for the record, I wasn't necessarily asking because I was having problems or anything installing Ubuntu on any particular computer.  I just wanted to know for the knowledge.  In the past I just always assumed if I downloaded an AMD64 architecture that I HAD to have an AMD processor and it would not work on an intel processor.  And then anything with an i or x in front of it was for Intel processors only.  From what I've read, that's not true.

---

### Post by LaRoza on 2007-11-23
> **fidelisprivatus said:**
> 
Oh and just for the record, I wasn't necessarily asking because I was having problems or anything installing Ubuntu on any particular computer.  I just wanted to know for the knowledge.  In the past I just always assumed if I downloaded an AMD64 architecture that I HAD to have an AMD processor and it would not work on an intel processor.  And then anything with an i or x in front of it was for Intel processors only.  From what I've read, that's not true.

Browsing Wikipedia might help, I find that to be very informative for potentially confusing topics like this.

---

### Post by jespdj on 2007-11-23
> **linuxonbute said:**
> Well yes - a vast difference.
an  i486 was 16Bit from the 1980's. Could only be used on motherboards which, if memory serves, could only handle hard discs of 32Megabytes ( NOT Gigabytes ) and a few Megabytes of memory.
AMD64 is 64Bit and pretty modern
No, the 80486 was not a 16-bit processor. It was a 32-bit processor that could potentially address 4 GiB of memory (although that was an incredible huge amount of memory in those days). See [Wikipedia: 80486](http://en.wikipedia.org/wiki/80486).

Intel's 80x86 processors have been 32-bit since the 80386. Linus Thorvalds originally started creating Linux on his 80386 computer in 1991.

---

### Post by linuxonbute on 2007-11-23
> **jespdj said:**
> No, the 80486 was not a 16-bit processor. It was a 32-bit processor that could potentially address 4 GiB of memory (although that was an incredible huge amount of memory in those days). See [Wikipedia: 80486](http://en.wikipedia.org/wiki/80486).

Intel's 80x86 processors have been 32-bit since the 80386. Linus Thorvalds originally started creating Linux on his 80386 computer in 1991.

Yes I know:oops: That was a typo. Been sat here too long.

---

