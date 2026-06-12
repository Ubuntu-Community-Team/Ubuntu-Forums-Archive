---
title: "Linux on ARM and CUDA?"
date: 2011-02-18
forum: Hardware
---

### Post by Bernie Gallagher on 2011-02-18
The latest buzz in the tech press is that ARM architecture and CUDA will supplant Intel x86 architecture in the future.  Will Ubuntu and other Linux distros be ready?

---

### Post by hsoulen on 2011-02-19
> **Bernie Gallagher said:**
> The latest buzz in the tech press is that ARM architecture and CUDA will supplant Intel x86 architecture in the future.  Will Ubuntu and other Linux distros be ready?

:lolflag:

Sorry, didn't mean to be a schmuck. These kinds of rumors abound my friend...

But seriously: [http://www.arm.com/community/software-enablement/linux.php]("http://www.arm.com/community/software-enablement/linux.php")

Cheers,

Hank

---

### Post by Bernie Gallagher on 2011-02-19
Glad to read that Linux is on top of current trends.  Thanks!

---

### Post by hsoulen on 2011-02-20
> **Bernie Gallagher said:**
> Glad to read that Linux is on top of current trends.  Thanks!

Absolutely!

Funny how in the "old days" it was Windows (NT) that was the king of architecture, used to run on Alpha/MIPS/Intel/PPC but they decided the winning architecture was x86-64... Although I think Win 2K8 might still support IA64 I am just not sure.

Linux on the other hand has just exploded with support for other architectures, if you have a platform there is a pretty good chance that you will find a Linux disto for it.

As for CUDA, it is a very specific processing paradigm that does not really translate well to general computing but does do very well on simple to mid-complexity tasks that benefit from massive parallel processing (compression/decompression come to mind which of course defines most of the heavy lifting in video decode/transcode). I don't see an OS running on it but I agree that outside of VDPAU video decoding it would be nice to see more support in Linux, that said it is still in its infancy even on Windows with only a few apps using for transcoding video.

ARM is a great architecture that is a solid choice for low-power solutions and you might just be right about it becoming a competitor, certainly a bunch of these architectures (ARM (includes the Apple A4 and Tegra) DragonBall etc.) are owning the tablet market and that market is certainly growing!

Reading:

ARM:[http://www.arm.com/]("http://www.arm.com/")
CUDA: [http://www.nvidia.com/object/what_is_cuda_new.html]("http://www.nvidia.com/object/what_is_cuda_new.html")

Cheers,

Hank

---

### Post by cascade9 on 2011-02-20
ARM and CUDA replace x86? I doubt it. It might take a some of the x86 market share, but its hardly going to knock x86 out. 

Besides the much lower performance from ARM, nvidia is harding for major trouble IMO. Intel wont licence nvidia to make iX  chipsets, AMD doesnt really want nvidia doing AMD chipsets (not that they will stop them....but nvidia hasnt made a new AMD chipset is many yewars now). Intel video is everywhere, killing off the low end of the GPU market that nvidia needs to survive, AMD is going to move to GPUs on CPUs like intel has. Bumpgate hurt them badly as well.....nvidia should be scared. 

> **hsoulen said:**
> Absolutely!

Funny how in the "old days" it was Windows (NT) that was the king of architecture, used to run on Alpha/MIPS/Intel/PPC but they decided the winning architecture was x86-64... Although I think Win 2K8 might still support IA64 I am just not sure.

The last windows version that will run on IA64 is Windows Server 2008 R2-

[http://blogs.technet.com/b/windowsserver/archive/2010/04/02/windows-server-2008-r2-to-phase-out-itanium.aspx](http://blogs.technet.com/b/windowsserver/archive/2010/04/02/windows-server-2008-r2-to-phase-out-itanium.aspx)

Redhat 5 will be the last Rehat version with IA64 support, 10.04 is the last canonical release to support IA64.

Itanium is pretty close to dead. 

The reason why x86-64 'won' is because of pricing.

---

### Post by Bernie Gallagher on 2011-02-20
> **hsoulen said:**
> ...massive parallel processing...

I think that's going to be the next big thing: massive parallel processing, with hundreds and maybe even thousands of cores on a single CPU, whether it be x86, ARM, CUDA, or the Playstation Emotion Engine :-p  Unless purely optical computers come soon, the speed of electricity itself is eventually going to slow advances of raw processor speed.

---

