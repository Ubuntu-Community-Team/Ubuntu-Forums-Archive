---
title: "Deep learning workstation"
date: 2023-05-07
forum: Hardware
---

### Post by som9591 on 2023-05-07
I have to buy PC for working on deep learning,Machine Learning projects. I need processor list that support Ubuntu 20.04, 22.04. 
If any one using high end configuration PC. Please, let me know configuration. 
Processor: 
RAM: 
Graphics: 
OS with version: 

If any ready to use PC available, links also welcome.

---

### Post by TheFu on 2023-05-07
Almost any CPU, motherboard, RAM and GPU will work with Ubuntu.  Ubuntu has an official supported server list.
You can spend $20,000 on a PC if you like or you can spend $75.

The main tips for finding well-supported hardware are this:
* Don't buy any hardware that was released in the last 12 months.  "New" hardware hasn't been out long enough for the Linux kernel guys to get support inside.  Some hardware features, like motherboard sensor data can take years to be supported.  If this is important to you, stay with Intel CPUs.
* The motherboard is probably more important than the CPU and RAM picked.  Some vendors are Linux-hostile and won't help troubleshoot **any** issues with a Linux computer. They aren't setup to help with Linux issues and haven't been interested in doing so ... er ... ever.
* On the motherboard, there are different addon chips like for a LAN or audio.  There are better vendors providing these LAN and audio chips across different lines of motherboards.  For example, Asus makes motherboards with both Intel and Realtek NICs onboard.  Intel NICs tend to be much better supported and generally cause fewer issues.  They tend to "just work" without any hassles.  But, they are slightly more expensive and get put into fewer motherboard models.  Realtek is the default NIC in most motherboards.  That's fine with Windows and usually ok with Linux, but not always.
* Anyway, supported RAM will be listed with the motherboard and CPU.  If you stick with that RAM, life will probably be much easier.  However, some RAM that isn't on the QVL can still work great.  But most motherboard vendors will not support you if you have RAM that isn't on their list.
* GPU - nvidia GPUs are more hassle than AMD with Linux.  For really high end GPUs, which some types of processing demand, the hassles and learning about drivers will be require to use nvidia.  OTOH, AMD GPUs have their support included with the kernel, so really new GPUs from AMD probably won't be in the 20.04 kernel lines ... or even in the 22.04 kernel lines.  You might be forced into using a 23.04 (non-LTS) install to get support until the new HWE kernel is released for 22.04.

I have 2 nearly identical systems here with AMD GPUs.  Support for those GPUs wasn't included in the kernels I was running (18.04 at the time), so I had to wait until 20.04 (really linux kernel 5.10) to get AMD driver support.  Prior to that, both ran with VESA GPU modes, which are fine for productivity stuff, but not for anything slightly demanding.  I don't game nor do I use GPUs for parallel processing. I can only imaging that having the proprietary driver would be very important for those tasks.  The VESA modes are enough for the light video editing that I do, but if I were a professional, then I'd probably want a $500-$1000 GPU.

I don't have any hands on with machine learning, but think it requires more RAM than anything.  That RAM needs to be in both regular system RAM and in lots of VRAM inside the GPUs.  So, I'd guess 64GB for system RAM and 12GB+ for GPU VRAM would be a target. There are cards with 24GB of VRAM.

Some vendors do sell Linux computers with pre-installed OSes and drivers. System76 is one of those.  People buy System76 for the excellent support. It isn't really about the Linux side, since almost any pre-built computer will run Linux.

Google found this: [https://www.pugetsystems.com/solutions/scientific-computing-workstations/machine-learning-ai/hardware-recommendations/](https://www.pugetsystems.com/solutions/scientific-computing-workstations/machine-learning-ai/hardware-recommendations/)  It looks to be over a year old.

If you want to trade money for expertise, I'd find a reputable Linux computer builder and speak with them on the options.  Most larger cities have a local computer builder that ships 10+ computers a day to local businesses and has 15+ employees. Just be certain they aren't 100% Windows-centric, since those people aren't familiar enough with Linux issues to build a good Linux system.

If you want more detailed help, you'll need to be much more specific. Budget would be the main concern for most people, but if you have $4000, then I suspect you could build an acquit system.  It will be harder with less budget and trade-offs will be needed, most likely in the GPU price/capability, since that will be the most costly single item inside the system.

---

### Post by mIk3_08 on 2023-05-08
> **som9591 said:**
> I have to buy PC for working on deep learning,Machine Learning projects. I need processor list that support Ubuntu 20.04, 22.04. 
If any one using high end configuration PC. Please, let me know configuration. 
Processor: 
RAM: 
Graphics: 
OS with version: 

If any ready to use PC available, links also welcome.

My Desktop works great from the moment I installed with Ubuntu 22.04 LTS 
So far so good and it was very smooth performance so far. Anyway, that was my set-up. 
Actually, it will depend on what / how you will be using on your machine. 
The application that you'll be installing to your machine. Regards and cheers.

Processor: ProceAMD Ryzen™ 9 5900HX 8 cores
Graphics: AMD Radeon™ Graphics 8
RAM: 16GB RAM
Storage: 512 SSD Storeage
Regards and cheers

---

### Post by TheFu on 2023-05-08
> **mIk3_08 said:**
> My Desktop works great from the moment I installed with Ubuntu 22.04 LTS 
So far so good and it was very smooth performance so far. Anyway, that was my set-up. 
Actually, it will depend on what / how you will be using on your machine. 
The application that you'll be installing to your machine. Regards and cheers.

Processor: ProceAMD Ryzen™ 9 5900HX 8 cores
Graphics: AMD Radeon™ Graphics 8
RAM: 16GB RAM
Storage: 512 SSD Storeage
Regards and cheers

Which deep learning tools are you using with this setup?

---

### Post by mIk3_08 on 2023-05-09
> **TheFu said:**
> Which deep learning tools are you using with this setup? Thanks TheFu for asking. My eldest child is using it for MATLAB. 
Regards and cheers.

---

### Post by BBQdave on 2023-05-09
> **som9591 said:**
> If any one using high end configuration PC. Please, let me know configuration.

My wife does financial analysis and accounting. Every couple of years she upgrades her computer, usually a Lenovo Thinkpad.

I get the old Thinkpad she was using and it works great with Ubuntu Linux. The last machine was a Lenovo Edge, though in the past they have been Thinkpads and currently she's using a Thinkpad - my future GNU/Linux machine :)

My hardware is in my signature :)

As stated by TheFu, hardware that is a couple years old works best, as the Linux Kernel will most likely have support packages for it.

If you can find a good deal on a two year old Lenovo Thinkpad, that's the way to go for solid GNU/Linux hardware :)

---

