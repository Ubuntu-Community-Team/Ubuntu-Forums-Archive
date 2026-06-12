---
title: "Dual Processor Support"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by manofsteel on 2005-06-27
I have an older Power Mac G4 dual 450, just wondering if Ubuntu would See and use both processors if not is thing anything I would have to do? Also is there a program that I could use to download songs to my iPod?

---

### Post by voidlogic on 2005-06-27
I don't know if this is the case for macs, but for PCs you can get the smp (multi-processor) kernel from the package manager, I'm rather sure its the same for PowerPC.

As for your ipod, Rhythmbox 0.8.8 now has iPod support. This may be play only,I know there are plently FAQs online, try google.

:) good luck

---

### Post by wookie on 2005-07-15
[QUOTE=voidlogic]I don't know if this is the case for macs, but for PCs you can get the smp (multi-processor) kernel from the package manager, 

How ?


Thanks, J/.

---

### Post by blitze on 2005-07-15
use synaptic and look at the kernel packages.  Worked for my dual AMD.

---

### Post by autocrosser on 2005-07-16
Look at synaptic--if you have enabled the extra repositories, you will find a 2.11 kernel that has PPC-SMP support--just fetch it & let synaptic set it up--I also use Gkrellm to monitor load on both---

Running a Dual 1G MDD

Cheers!!
Dean

---

### Post by MonolithTMA on 2005-12-07
[QUOTE=autocrosser]Look at synaptic--if you have enabled the extra repositories, you will find a 2.11 kernel that has PPC-SMP support--just fetch it & let synaptic set it up--I also use Gkrellm to monitor load on both---

Running a Dual 1G MDD

Cheers!!
Dean[/QUOTE]

I know this is an older thread, but I have a Dual 1.25 G4 MDD I tried the latest PPC-SMP kernel and it would no longer boot into Ubuntu. Fortunately, I figured out how to boot to the *old* kernel and managed to make that the main one again. I'm a total newbie and I've been running Ubuntu since this last Sunday without any problems. I'm going to try and install the SMP kernel again on Saturday. It would be nice if there was an Ubuntu Live image with the PPC-SMP kernel on it so I didn't have to jump through so many hoops to test this. :???:

Edit: I'm running Breezy BTW.

---

### Post by MonolithTMA on 2005-12-07
Ok, I think I was using the linux-image-2.6.12-10-powerpc64-smp instead of the regular linux-image-2.6.12-10-powerpc-smp. Silly me. I installed linux-image-2.6.12-10-powerpc-smp and it worked like a charm. :KS

---

