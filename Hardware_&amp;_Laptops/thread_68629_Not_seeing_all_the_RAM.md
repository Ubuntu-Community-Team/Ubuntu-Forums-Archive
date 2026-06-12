---
title: "Not seeing all the RAM"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by atatistcheff on 2005-09-23
Just installed Hoary Hedgehog on an Intel PC with 6GB of RAM, however the OS is seeing less than a GB.  Here's the output of the free -m command:

             total       used       free     shared    buffers     cached
Mem:           885        190        694          0          8         90
-/+ buffers/cache:         91        793
Swap:         2588        113       2475

Am I missing something?  How do I get it to see the additional RAM?

Thanks,
Alex

----------------------- update --------------------

I installed the 686 SMP kernel because this is a dual proc machine and now it's seeing more RAM.  However, it's still not up to the 6GB mark.  Here's the output of free -m now:

             total       used       free     shared    buffers     cached
Mem:          3291       2614        676          0         39       2368
-/+ buffers/cache:        206       3084
Swap:         2588          0       2588

Any ideas would be appreciated - thanks!

---

### Post by mlomker on 2005-09-23
32-bit versions of linux are limited to 4 Gigs of RAM.  

My system has one Gig and that command shows 999.  I assume that it can't see the ramdisks that are set up prior to system boot.

What does **dmesg | grep Memory** give you?

---

### Post by El Cubano on 2005-09-23
[QUOTE=][/QUOTE]
 32-bit machines can see up to 64 GB if they are running on a CPU that supports 36-bit PAEs and have the CONFIG_HIGHMEM64G=y set in the kernel configuration.  To even see more than 1 GB you at least need CONFIG_HIGHMEM4G=y set.

---

### Post by mlomker on 2005-09-23
> 32-bit machines can see up to 64 GB if they are running on a CPU that supports 36-bit PAEs and have the CONFIG_HIGHMEM64G=y set in the kernel configuration. 

That's interesting but I'm assuming that the poster is running a stock Ubuntu kernel.

---

### Post by atatistcheff on 2005-09-23
Thanks for the info.  I just started at this job and inherited this computer.  It's a dual proc Xeon and I'm wondering if it might be 64 bit capable?  I noticed that Intel did start selling a 64 bit Xeon procs about a year ago.  Is it possible this machine is one of them?  What would be a way Ubuntu would tell me?

Thanks!
Alex

---

### Post by mlomker on 2005-09-23
> Is it possible this machine is one of them?  What would be a way Ubuntu would tell me?

I can't offer you an authoritative answer--I just did some searches here and on Google to try to figure it out but I'm having trouble finding solid documentation.  What I've found so far suggests that only the amd64 build supports more than 4 Gigs.  I'll keep poking around and see what I can find.

Edit:  Just found this in a Google search: > For people with 4 GB probems–are you running a 32-bit Linux system or a 64-bit system? If it’s 32-bit, then make sure that the kernel is compiled with support for the highest amount of memory (I think it’s 64 GB, but I’m to lazy to check right now). The default is usually 4 GB these days, but that includes PCI I/O space and a bunch of other things, so you don’t actually get all 4 GB of RAM. Increasing the kernel’s limit to 64 GB will make it run a bit slower, but you’ll have access to all your RAM.

I think you'll need to compile a custom kernel to see more than 4 Gig, just like El Cubano said.

---

### Post by atatistcheff on 2005-09-26
Thanks for the help.  For now, this is working much better since it's using over 3GB of RAM.  I'll probably reserve the recompiling for sometime when I'm a bit more ambitions.

Thanks!
Alex

---

