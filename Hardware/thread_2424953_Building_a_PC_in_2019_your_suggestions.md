---
title: "Building a PC in 2019: your suggestions"
date: 2019-08-18
forum: Hardware
---

### Post by vitaly-zdanevich on 2019-08-18
Good day, during this week I need to choose and buy my new PC, maybe for the next 10 years, who knows :) so obviously I want to choose the best one for my money. I am a software developer, I am not playing video games, but I need my browser works fast, with hardware acceleration :)

Sometimes I will need to run virtual machines in VirtualBox - with Windows inside and Linux.

And for this system or maybe later, when I really will need it - GPU with Cuda may be important detail, maybe I will need Cuda for AI projects, also good to have it for faster video editing (in open source video editor Shotcut).

I think that for now 16 or 32 GB of RAM will be enough for me, but maybe in the future it will be useful to have an option to upgrade for 64 GB of RAM on the same motherboard.

What CPU is better for Linux nowadays? Especially with Meltdown/Spectrum patches. What socket do you think I need to choose? Motherboard is the most important part.

Also I want to use 3 display as minimum, maybe more in the future.

Right now I am doing research on my own about all this stuff, but just posting here if some of you have something to say about this big world of computer hardware, I do not want to do some mistakes.

Thank you.

---

### Post by TheFu on 2019-08-18
Ryzen has the best value today, by far.
I don't know anything about CUDA.

Impossible to make suggestions beyond that from the information provided.  The RAM seems fine, but in 3 yrs, DDR4 will be dead and buying more RAM after that will be harder, more costly.

If you want better virtual machine support, don't use virtualbox. Use KVM+virt-manager.

You didn't say which language(s) you expect to program using.  Anything except Java doesn't need THAT much RAM.

Professional developers tend to replace their machines every year or two just to get the performance improvements. Time is money.

---

### Post by MartyBuntu on 2019-08-18
> **TheFu said:**
> Ryzen has the best value today, by far.


Agreed. More cores and a healthy amount of RAM (16 gigs or more).

If you're doing some heavy virtualisation, maybe look into Threadripper. Their price has come down a bit.

---

### Post by CatKiller on 2019-08-18
> **vitaly-zdanevich said:**
> And for this system or maybe later, when I really will need it - GPU with Cuda may be important detail, maybe I will need Cuda for AI projects, also good to have it for faster video editing (in open source video editor Shotcut).

CUDA is Nvidia-specific. If you actually *need* CUDA, rather than playing around with OpenCL, that's quite a constraint.

Shotcut can use VA-API as well as nvenc, so you'll have GPU acceleration for whatever hardware you use.

---

### Post by TheFu on 2019-08-18
I have a Ryzen 5 2600 (12 threads) with 16G or RAM running 6 VMs 24/7.  Over 8G of RAM is available and the CPU use is seldom over 30%, usually under 10%.  I plan to move a heavy Windows VM over soon, just need to ensure the VM motherboard presented to the guest doesn't change as I move between different Ubuntu releases in the process.  The VM was created in 2010 and have been migrated to 2 other systems without issues.  Most of the other VMs have been migrated/updated too, but Linux isn't picky like Windows.

A Ryzen 5 1600 was US$80 here at retail last month which is almost the same performance level as the Ryzen 2600.  For under $200, I think I could build a failover VM server to replace the 1st generation Core i5 I'm currently using.  That Core i5 was the primary VM host here since 2010.

But I'm hosting corporate services for a few small businesses, not heavy compute processes.  Everyone has slightly different workloads.
In 2012, I did Android development inside a VM. It was painful.  I was a cross platform C++ dev in the 1990s.  Java is entirely different when it comes to bloat as compared to every other language I've used. That list is pretty long - over 30 languages.  By far, java is the heaviest, most bloated, demands the fastest CPUs with the most RAM possible.  Development for C++ is fine on 4G of RAM, unless you are doing GUI programs, then 8G is fine.  That applies to all the C++-like languages ... C#, Rust, etc.  All the scripting languages are good on half that, except for the very largest projects.  If you are doing huge projects, look into serverless computing to break things up and add scalability were it is needed.

Sorry - didn't mean to go so far off topic.

---

### Post by lammert-nijhof on 2019-08-18
I run Virtual Machines on a Ryzen 3 2200G with 16GB of memory. I love Virtualbox, I use QEMU/KVM too, its disk IO is faster, but Virtualbox is more user-friendly and far more robust. Looking at your requirements I would go for 32GB and the fastest Ryzen CPU you can afford. I'm happy with my Ryzen 3, but updating Windows 7 and 10 at the same time maxes out my CPU occasionally for a minute or so. I'm happy with 16GB, but once a week when running a Linux OS, Windows 7 and 10, my 4GB ZFS memory cache is reduced slightly to free memory for the VMs. 

I would consider using ZFS file-system, especially with the new Ubuntu 19.10. I use it also for my Virtual Machine datapool (partitions) and my response times are instantaneous due to a 4GB memory cache. I reboot Linux OSes in 6 - 10 seconds and that could be helpful during testing too. Other useful advantages are snapshots, compression, full software raid support and protection against file corruption due to Copy On Write (COW)

---

### Post by Autodave on 2019-08-20
Definitely Ryzen.  If you must have Cuda, the Nvidia is your only choice.  I have an RTX 2070 8 gig which is fantastic.  And, the price is coming down, though still not cheap.  the 1080s and 1060s have dropped significantly lately.

---

### Post by oldfred on 2019-08-20
You may need newer UEFI/BIOS.
       AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2) 
    
And be sure your motherboard supports chip.
AMD is sending out old chips for some new older version motherboards, so you can update UEFI/BIOS to be able to run the newest chip that motherboard was designed for as upgrade. Brand new motherboard without chip cannot be updated.

---

