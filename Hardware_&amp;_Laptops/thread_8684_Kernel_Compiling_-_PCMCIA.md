---
title: "Kernel Compiling - PCMCIA"
date: 2004-12-20
forum: Hardware &amp; Laptops
---

### Post by Vesperan on 2004-12-20
(Edit: If moderators feel this better belongs in the laptop support forum, please move it - I originally decided to post in this forum as I was going to ask other, non-pcmcia/laptop questions, but decided against it)

Hi,
a few days ago I installed Ubuntu 4.10 on my Dell 600m laptop. Everything (even cpu frequency scaling on the Dothan cored P-M, which is a first for a distribution) worked fine except for wireless, and sound.

The wireless I am not so concerned about, but after going through these forums for a solution to why no sound card was detected, I found posts saying that it was due to the ramdisk being used and conflicting irqs (other laptop users with same sound solution had the exact same problem). The solution would be to recompile the kernel with file system support built in, and disable the initrd reliance. Easy enough I thought, but after running into a few unexpected problems that took most of a day I still haven't got there. 

Currently I have a kernel based on the linux-sources 2.6.8.1 that has been configured by myself (and is very different from the default, which had a large number of modules). Everything in the bootup process will work fine, until it gets to starting PCMCIA services, where at it will then halt permanently. Whereas on a default kernel it will say ok and load fine. Wireless wont work, but it says ok and continues booting, which is all I'm asking of it for the time being.

Comparing the two configs with regards to PCMCIA (in bus options -> pcmcia and device drivers -> networking support -> wireless lan) shows that both configs have near identical settings - all I did was remove a few modules that I knew would not be used. The PCMCIA card I have is Intel 2200BG, so I felt it safe to remove the modules such as Aviator/Raytheon 2.4mhz wireless support for example. 

When compiling the kernel I followed the how-to in the Wiki (as opposed to manual make and modules install): [http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto)

Now, what I want to know is:

1. Did I mess up a kernel option somewhere that is stopping the 'starting pcmcia services' from completing, or at the least not entering a permanent loop/crashing. If so, where? Or is there something I forgot to do somewhere else that has caused this.

2. While I want to keep the pcmcia services in the boot up sequence if at all possible as I will be using it, how can I remove it should it be too big a problem? A quick check suggests making the /etc/rc*d/ files relating to pcmcia non-executable (either through permissions or deletion), there are entries for pcmcia in three directories - do I do it for all? Is there another way to remove the service, for example an interactive boot sequence (as in Fedora) where I can say yes/no to each - just so I can go through and see if the kernel will boot fine aside from this problem.

I would search for these answers and no doubt fine themself, but it is getting too late for such things - and I've had enough fun doing searches through forums, Google, and wherever answers may lurk today. Forgive me if some questions seem a bit newbiesh, and thanks in advance!

---

### Post by Vesperan on 2004-12-20
Update.

I followed my own advice and set the permissions such that pcmicia services could not start. This avoided the stalling the problem, and everything boots fine - and sound works, thankfully. However, when loading with that kernel the entire booting sequence feels much slower than the default 686 kernel (in custom kernel the processor type is set to Pentium-M). 

For now however, I am content - I will leave getting pcmcia wireless going to another day.

---

