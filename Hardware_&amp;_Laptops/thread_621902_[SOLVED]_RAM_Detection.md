---
title: "[SOLVED] RAM Detection"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by Zer0d on 2007-11-24
I just installed 4x(Crucial DDR2 BallistiX PC8500 1024MB CL5) because the two others I had before became corrupt. In BIOS my computer detects 4GB RAM but in Ubuntu it can only find 3GB, why is that?

```
root@zer0d-desktop:~# free -m
             total       used       free     shared    buffers     cached
Mem:          3035        429       2605          0         12        236
-/+ buffers/cache:        181       2854
Swap:         4769          0       4769

```

One more question, are these voltages too low?
```

DDR2 Voltage 1.87V
DDR VVT Voltage 0.93V
```

---

### Post by PmDematagoda on 2007-11-24
Simple but important question, do you have Ubuntu 64 bit or Ubuntu 32 bit?

---

### Post by Zer0d on 2007-11-24
I have Ubuntu 7.10 32bit version.

---

### Post by Zer0d on 2007-11-24
I was reading this**[ link ]("http://linux-mm.org/HighMemory")**and maybe this part is why it only shows 3GIG?
[B]
Currently the 32 bit x86 architecture is the most popular type of computer. In this architecture, traditionally the Linux kernel has split the 4GB of virtual memory address space into 3GB for user programs and 1GB for the kernel.[/B]

---

### Post by PmDematagoda on 2007-11-24
Well, I am not sure if that article is right (1 Gb of RAM for the kernel itself is impossible unless the kernel they used has technology which is about 30 light years ahead of the current kernels:)), but you will need Ubuntu 64 bit in order to use all 4 Gb of your RAM or you will have to compile a 32 bit kernel which supports a maximum of 4 Gb itself.

---

### Post by Zer0d on 2007-11-24
Thanks for informing me :) Think I will just stay put with the 32bit system because last time I tried 64bit system I couldn't get it installed.

---

### Post by PmDematagoda on 2007-11-24
As it is a real shame to leave 1 Gb of RAM all alone to just waste away (I have only 1 Gb of RAM myself:)), it would be better for you if you could install and use Ubuntu 64 bit(You can also try compiling a suitable kernel but I do not have much experience concerning that), could you post exactly what problems you get, what you tried and anything else that may be required.

---

### Post by Zer0d on 2007-11-24
I will give it another try now :) Last time I tried 64bit it was with Ubuntu version 7.04, all I remember is that I wasn't able to install with the live cd. As you said it would be a shame to leave out 1GB of RAM . Why is the 64bit version named AMD64 by the way? I never could understand that because I have Intel 64bit processor but there is no Ubuntu version with that name.

---

### Post by PmDematagoda on 2007-11-24
The 64 bit iso is named AMD64 since it was AMD that first introduced 64 bit technology, and because Intel followed AMD with EM64T which is very similar to AMD64, so there was no necessity for a seperate iso to be created specifically for Intel's 64 bit technology.

---

### Post by Zer0d on 2007-11-24
Now my new 64bit Ubuntu is up running :D Now it finds all the RAM, so thanks a lot for motivating me to try 64bit again and clarifying things :D

---

### Post by PmDematagoda on 2007-11-24
Great to see 64 bit now works for you without a hitch and that you are enjoying the full benefits of all 4Gb of RAM:), glad I was able to motivate you:D.

---

