---
title: "64 Bit Vs 32 Bit"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by texas.chef94 on 2009-08-25
Recently activated an older hp notebook which is 32 bit. It does have 1GB RAM if that is relevant.
1. Can I install 64 Bit OS to this unit

---

### Post by Malta paul on 2009-08-25
It may work, but maybe you would like to check this out:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

Have fun :)

---

### Post by Malta paul on 2009-08-25
I should have mentioned if your CPU will run a 64bit system a 'core two' onwards.;)

---

### Post by dE_logics on 2009-08-25
Most probably it will.

---

### Post by mlentink on 2009-08-25
> **dE_logics said:**
> Most probably it will.
Most probably it will [I][B]not.
[/B][/I]You must have a 64-bit system to be able to run a 64-bit operating system***. ***Check the processor of that older notebook. If it has anything less than a Core2 Duo or AMD64 processor, it will not run the 64-bit version[I][B].
[/B][/I]The OP specifies that the system is 32-bit, which basically answers his own question.

---

### Post by howefield on 2009-08-25
> **texas.chef94 said:**
> Can I install 64 Bit OS to this unit

You said it is an HP, can you tell us exactly what the model/number is ?

I have a 64 bit capable HP (5 years old) which was shipped with a 32 bit operating system, there are probably millions like it. Now running Ubuntu 9.04 64 bit on it.

---

### Post by HavocXphere on 2009-08-25
Unlikely. Depends on your idea of "old".

> hp notebook which is 32 bit
If the hp notebook is designed for 32b only then 64 will definitely not work.

Just go with 32bit. The benefits of 64 fairly modest and probably close to zero on an old laptop.

---

### Post by texas.chef94 on 2009-08-25
> **HavocXphere said:**
> Unlikely. Depends on your idea of "old".


If the hp notebook is designed for 32b only then 64 will definitely not work.

Just go with 32bit. The benefits of 64 fairly modest and probably close to zero on an old laptop.

Thank you so much. Appreciate heads up

---

### Post by presence1960 on 2009-08-25
> **howefield said:**
> You said it is an HP, can you tell us exactly what the model/number is ?

I have a 64 bit capable HP (5 years old) which was shipped with a 32 bit operating system, there are probably millions like it. Now running Ubuntu 9.04 64 bit on it.

+1
I have an HP a810n with 32 bit XP Home that was given to me as a gift almost 5 years ago. It has an Athlon 64 2.4 GHz CPU - so I installed Ubuntu 64 bit on it. **Only one thing determines if you can run 64 bit - your CPU. if you aren't sure look up your CPU at the manufacturer's web page.**

---

### Post by running_rabbit07 on 2009-08-25
I have a 64-bit system but the 32-bit OS works much better.

---

### Post by roystreet on 2009-08-25
Question for you...Does 32bit have a ram limitation like it does in windows?  I think the limit for windows 32bit is 3 or 4 gb & you will have to go to 64bit to use more ram.  I didn't know ubuntu has that same cap.  

Thanks,
~roystreet

---

### Post by texas.chef94 on 2009-08-25
> **presence1960 said:**
> +1
I have an HP a810n with 32 bit XP Home that was given to me as a gift almost 5 years ago. It has an Athlon 64 2.4 GHz CPU - so I installed Ubuntu 64 bit on it. **Only one thing determines if you can run 64 bit - your CPU. if you aren't sure look up your CPU at the manufacturer's web page.**

These are specs of my HP 2590US except I upgraded RAM to 1GB
Please advise what is and is not possible with this unit

Presario 2590US
System Specs
Type of system: 	Laptops
Bus Architecture: 	USB/PCMCIA
Hard Drive Bus: 	EIDE
Native OS: 	Windows XP Home
CPU Type: 	2.3GHz Intel Mobile Pentium 4
Memory Specs
Standard Memory: 	256 MB (removable)
Maximum Memory: 	1.0 GB
Memory Expansion: 	2 sockets
Memory Comments: 	PC2100 DDR SDRAM SODIMMs

---

### Post by running_rabbit07 on 2009-08-25
> **roystreet said:**
> Question for you...Does 32bit have a ram limitation like it does in windows?  I think the limit for windows 32bit is 3 or 4 gb & you will have to go to 64bit to use more ram.  I didn't know ubuntu has that same cap.  

Thanks,
~roystreet

I don't think you could need more than 4 gigs with Ubuntu unless it is a server. I have 2 gigs and can have every program running and a whole book worth of PDFs and still not overflow to SWAP.

---

### Post by AlexDudko on 2009-08-25
> **texas.chef94 said:**
> These are specs of my HP 2590US except I upgraded RAM to 1GB
Please advise what is and is not possible with this unit

Presario 2590US
System Specs
Type of system: 	Laptops
Bus Architecture: 	USB/PCMCIA
Hard Drive Bus: 	EIDE
Native OS: 	Windows XP Home
[COLOR="DarkOrange"]CPU Type: 	2.3GHz Intel Mobile Pentium 4[/COLOR]
Memory Specs
Standard Memory: 	256 MB (removable)
Maximum Memory: 	1.0 GB
Memory Expansion: 	2 sockets
Memory Comments: 	PC2100 DDR SDRAM SODIMMs

Only a 32-bit one.

---

### Post by scorp123 on 2009-08-25
> **roystreet said:**
> ...Does 32bit have a ram limitation like it does in windows?

32-bit CPU means:  CPU can address 2^32 Bytes = 4294967296 Bytes.
In GigaBytes: 4294967296/1024/1024/1024 = **_4_**

There's your 32-bit memory limit. 4 GB. So everything that has to do with memory (RAM + memory of your graphics card) has to fit within those 4 GigaBytes of addressable memory. That's why on most system you will see something between 3.2 to 3.6 GB of RAM, the difference is what the graphics card needs for itself to function.

There is a possible workaround: "PAE" = Physical Address Extension. With that your 32-bit kernel can address up to 64 GB of RAM ... but it comes at a 10% - 15% performance penalty.

Distros such as CentOS, RHEL and OpenSUSE ship with the "PAE" feature activated in their 32-bit variants so I'd assume the performance can't that bad, despite this theoretical performance penalty.

64-bit OS have a theoretical memory limit of 2^64 = 18446744073709551616 Bytes.

... that's 17179869184 GigaBytes. Or 16'777'216 TeraBytes. So that's a lot. 

But it explains why 64-bit OS can address more memory than a 32-bit OS.


> **roystreet said:**
>  I didn't know ubuntu has that same cap. The laws of physics apply to Ubuntu too. Newton, Einstein, Hawking ... you better not defy them and abide by their laws :D ....

---

### Post by presence1960 on 2009-08-25
> **running_rabbit07 said:**
> I have a 64-bit system but the 32-bit OS works much better.

that is a limitation for all 32 bit OSs unless they have PAE enabled, which in my opinion isn't worth it to gain .8 MB RAM or less on a system.

32 bit generally will see 3.2 GB RAM, but the rest isn't wasted it is alloted for use in other areas such as video graphics.

---

### Post by scorp123 on 2009-08-25
> **presence1960 said:**
> that is a limitation for all 32 bit OSs unless they have PAE enabled, which in my opinion isn't worth it to gain .8 MB RAM or less on a system. True. It only pays off if you have a 64-bit CPU and e.g. 8 GB RAM in your system but for some stupid reasons _MUST_ use Linux in 32-bit, e.g. because some commercial software you _HAVE TO_ use for your job is not available in a native 64-bit version.

This was pretty much the scenario I was caught in. Until tonight :D  Now it's reinstall time and this time I can finally switch to 64-bit Ubuntu :D

---

