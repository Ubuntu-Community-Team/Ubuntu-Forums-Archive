---
title: "Dell D620 runs hot (Intel graphics)"
date: 2010-05-02
forum: Hardware
---

### Post by sgarman on 2010-05-02
Hello,

After upgrading to Lucid Lynx I've noticed a couple of regression bugs on my Dell D620 laptop. For one, the fan is not coming on as frequently as it used to and as a result the laptop is running very hot. The CPU is getting up to 80 C during compiles according to sensors-applet.

Other threads on this topic place the blame on open source video drivers for ATI and Nvidia cards, but this machine has an Intel video chipset and the open source version is the one officially supported by Intel.

Is anyone else encountering this? If I wanted to report it as a bug, which component would I file it under - presumably the kernel?

Scott

---

### Post by linucksnOOb on 2010-05-03
Scott I'm having the same problems with 10.4.  This is my first experience with any Linux distro so I don't know what to think.  I definitely enjoy it better than windows but the heat simply is overwhelming my poor little box using the Intel gma965 chipset.
 
On the other hand I've also tried the BT4 distro and experienced no problems with heat whatsoever and was quite pleased with it after updating and installing additional packages.  I'm not sure but I think they may be two different kernels so if I was you I would try a different distro or a different kernel until someone more knowledgable addresses this problem.

---

### Post by Jimtheplanner on 2010-05-03
Hi Guy's,

I also have a bit of heat running a Dell 1545 (64) just under the hard drive area (left hand palm rest). 

I also get intermittent "flashes" across my screen almost like a hesitant screen refresh.

Jim

---

### Post by UbuNoob001 on 2010-05-03
> **Jimtheplanner said:**
> Hi Guy's,

I also have a bit of heat running a Dell 1545 (64) just under the hard drive area (left hand palm rest). 

I also get intermittent "flashes" across my screen almost like a hesitant screen refresh.

Jim

:  I also have a Dell 1545 (64) running 10.04_64 and experience the same problems: 

Check your process monitor. Mine spikes/overheats when using Java and Npviewer.bin. As well as generally higher temperatures overall (sits at 54C, spikes to 70C).

---

