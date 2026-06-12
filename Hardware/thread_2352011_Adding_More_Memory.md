---
title: "Adding More Memory"
date: 2017-02-08
forum: Hardware
---

### Post by daniell59 on 2017-02-08
Currently I am running Ubuntu 14.04 32 with 2 GIGs of memory. I am thinking of upgrading to 4 GIGs. I am wondering whether I will see an improvement, or should I just build a new computer.

---

### Post by Autodave on 2017-02-08
With the 32 bit system, I doubt that you will see any difference. Having said that, I am assuming everyday normal usage.  However, if you are into gaming or spread sheets, then you would probably notice a difference because the HD would not be swapping out as often.

---

### Post by daniell59 on 2017-02-08
Currently I have one problem. When I do too many things at once, the screen turns dark for a few seconds, then returns to normal. I am wonder whether adding more memory would solve this problem

---

### Post by Autodave on 2017-02-09
Again, I doubt it. But, it always could. Sounds more to me like a video issue: wrong driver or card failing. Could also be an overheating problem to the memory, CPU, or GPU.

You could bring up the task manager and see what is going on. If the "swap" part is going high, then more memory could be your solution.

What are the specs on the machine and what version are you running? If you are running Ubuntu, you may want to try and put the Xubuntu desktop on the machine: that alone will save a lot of memory and speed.

---

### Post by daniell59 on 2017-02-09
system      N68SA-M2S ()
                              bus         N68SA-M2S
                              memory      128KiB BIOS
cpu@0                         processor   AMD Athlon(tm) 64 X2 Dual Core Process
                              memory      128KiB L1 cache
                              memory      512KiB L2 cache
                              memory      2GiB System Memory
                              memory      1GiB DIMM DDR2 533 MHz (1.9 ns)
                              memory      1GiB DIMM DDR2 533 MHz (1.9 ns)
                              memory      DIMM DDR2 533 MHz (1.9 ns) [empty]
                              memory      DIMM DDR2 533 MHz (1.9 ns) [empty]
cpu@1                         processor   
                              memory      128KiB L1 cache
                              memory      512KiB L2 cache
pci@0000:00:00.0              memory      RAM memory
pci@0000:00:01.0              bridge      MCP61 LPC Bridge
pci@0000:00:01.1              bus         MCP61 SMBus
pci@0000:00:01.2              memory      RAM memory
pci@0000:00:02.0              bus         MCP61 USB 1.1 Controller
pci@0000:00:02.1              bus         MCP61 USB 2.0 Controller
pci@0000:00:04.0              bridge      MCP61 PCI bridge
pci@0000:00:05.0              multimedia  MCP61 High Definition Audio
pci@0000:00:06.0              storage     MCP61 IDE
pci@0000:00:07.0  eth0        bridge      MCP61 Ethernet
pci@0000:00:08.0              storage     MCP61 SATA Controller
pci@0000:00:08.1              storage     MCP61 SATA Controller
pci@0000:00:09.0              bridge      MCP61 PCI Express bridge
pci@0000:02:00.0              display     RV620 LE [Radeon HD 3450]
pci@0000:02:00.1              multimedia  RV620 HDMI Audio [Radeon HD 3400 Serie
pci@0000:00:0b.0              bridge      MCP61 PCI Express bridge
pci@0000:00:0c.0              bridge      MCP61 PCI Express bridge
pci@0000:00:18.0              bridge      K8 [Athlon64/Opteron] HyperTransport T
pci@0000:00:18.1              bridge      K8 [Athlon64/Opteron] Address Map
pci@0000:00:18.2              bridge      K8 [Athlon64/Opteron] DRAM Controller
pci@0000:00:18.3              bridge      K8 [Athlon64/Opteron] Miscellaneous Co
                  scsi1       storage     
scsi@1:0.0.0      /dev/sda    disk        160GB ST3160812AS
scsi@1:0.0.0,1    /dev/sda1   volume      53GiB Windows NTFS volume
scsi@1:0.0.0,2    /dev/sda2   volume      95GiB Extended partition
                  /dev/sda5   volume      2044MiB Linux swap / Solaris partition
                  /dev/sda6   volume      93GiB Linux filesystem partition
                  scsi3       storage     
scsi@3:0.0.0      /dev/cdrom  disk        DRW-2014L1T

If increasing the memory would help, I would then install Ubuntu 16.04 64.

---

### Post by lammert-nijhof on 2017-02-10
I agree with autodave, First check the size of your swap file in e.g. the system monitor. If it is getting in the hundreds of MB, you could do two things: Enable zswap and change swappiness to e.g. 25, but for both you will have to use the command line. You could also buy more memory, 2 sticks otherwise you loose the speed advantage of the dual access to memory. Default the swappiness parameter is set to 60, which means that the system starts considering swapping, if 40% of the memory is in use. By setting swappiness to 25, it will start considering swapping after 75% of the memory has been occupied. If you use zswap, it will use compression and an area in memory to swap to. Probably zwap could make very good use of that last part of memory to store swapped out compressed programs. If your current swap is e.g. 500 MB, zswap would compress it to 250 MB or less and could keep it in the swap area in memory. 

I have done the same on my 8 year old system with AMD 3-core processors and 4 GB of memory. I will not do it, but I have the feeling that I can delete the disk swap partition. It is not used anymore.

---

### Post by daniell59 on 2017-02-10
Thanks guys for your informative replies.

What is the significance of this?

Swap
529.3 Mib (25.9%) of 2.0 GiB

At some point I will build another computer. In the mean time, I would like to get as much out of this one as I can.

---

### Post by mikewhatever on 2017-02-10
Yes, definitely more RAM, if you want to keep using that PC for a few more years. Just make sure to check the board's max capacity: 
```

sudo dmidecode -t memory

```

---

### Post by daniell59 on 2017-02-10
The maximum memory that this MB will take is 8GIGs. It has only two slots. I would have to replace both with new memory. I wonder whether it is worth doing, or should I just build a new computer.

---

### Post by Autodave on 2017-02-10
That memory should be cheap enough. Just make sure that all 4 sticks match as far as speed. That would be quicker and cheaper than a new machine.  The only thing that bothers me about doing that is the display going dark: while low resources *could* cause that to happen, it rarely does.

---

### Post by mikewhatever on 2017-02-10
I can't possibly say if it's worth it for you or not. This is something you need to decide for yourself. Personally, I've done it a lot, and see no reason to stop.

---

### Post by daniell59 on 2017-02-11
I can't possibly say if it's worth it for you or not. This is something you need to decide for yourself. Personally, I've done it a lot, and see no reason to stop.
As I previously mentioned, the screen darkens when I have too many activities going on at once. If I was reasonably sure that the added memory would solve that problem, I would certainly add more. 
Thank you for your input.

---

### Post by Yellow Pasque on 2017-02-11
I think I would try a LiveUSB of Ubuntu 16.04.1 and try to reproduce the screen darkening behavior

> The maximum memory that this MB will take is 8GIGs. It has only two slots.

A 4GB stick might be harder to come by and have a price premium over two 2GB sticks. 
1GB and 2GB sticks were a lot more common back in the DDR2 era if memory serves correctly.

---

### Post by daniell59 on 2017-02-11
> **Temüjin said:**
> I think I would try a LiveUSB of Ubuntu 16.04.1 and try to reproduce the screen darkening behavior



A 4GB stick might be harder to come by and have a price premium over two 2GB sticks. 
1GB and 2GB sticks were a lot more common back in the DDR2 era if memory serves correctly.

I would buy two 2GIG modules.

---

### Post by daniell59 on 2017-02-11
I think I would try a LiveUSB of Ubuntu 16.04.1 and try to reproduce the screen darkening behavior

As per your suggestion I tried a live DVD Ubuntu 16.04 64. I could not reproduce the screen darkening behaviour. I am not sure of the significance of this. I did not run it very long.

---

### Post by daniell59 on 2017-02-13
I just realized something that helped me decide not to add more memory. My cpu MHz is only 1000. For Ubuntu 16.04 2000 is recommended. My board wont support more than 1000.

---

### Post by Yellow Pasque on 2017-02-13
> My cpu MHz is only 1000. ... My board wont support more than 1000. 

False. You're probably looking at the idle speed or the speed of the HT link. The slowest Athlon 64 X2 ever made was 1.9GHz

Look at:
```
cat /proc/cpuinfo
```

---

### Post by daniell59 on 2017-02-13
> **Temüjin said:**
> False. You're probably looking at the idle speed or the speed of the HT link. The slowest Athlon 64 X2 ever made was 1.9GHz

Look at:
```
cat /proc/cpuinfo
```

physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv vmmcall
bogomips	: 4621.26
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

daniel@daniel-N68SA-M2S:~$ 

I don't see the speed listed here. Maybe I am missing something.
Thanks for your input.

---

### Post by daniell59 on 2017-02-13
This looks like the speed to me.

daniel@daniel-N68SA-M2S:~$ lscpu | grep -i mhz
CPU MHz:               1000.000
daniel@daniel-N68SA-M2S:~$

---

### Post by Yellow Pasque on 2017-02-13
> I don't see the speed listed here. Maybe I am missing something.

It looks like you cut off the important part of the output(s), which is the model number. Nevertheless, from bogomips number, I'd guess you have a 2.3GHz CPU (maybe Athlon 64 X2 4400+)

> This looks like the speed to me.
Again, that is the idle speed. It will throttle up to full speed when you do something intensive, unless you have it locked into powersave mode.

---

### Post by daniell59 on 2017-02-13
> **daniell59 said:**
> I just realized something that helped me decide not to add more memory. My cpu MHz is only 1000. For Ubuntu 16.04 2000 is recommended. My board wont support more than 1000.

Thank you for you informative reply. It has been a very long time since I built a computer, and there are many gaps in my knowledge.
I think that I have more information about the processor. model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ Is the 4400 referring to the speed?
I would appreciate it if you could explain this to me. The MB manual says FSB: supports up to 1GHz Bandwidth.
Thanks for the assistance. This is a learning experience for me.

---

### Post by Yellow Pasque on 2017-02-13
We're getting way outside the scope of your original question.

> model name : AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ Is the 4400 referring to the speed?

Sort of. [https://en.wikipedia.org/wiki/Performance_Rating](https://en.wikipedia.org/wiki/Performance_Rating)

> The MB manual says FSB: supports up to 1GHz Bandwidth

This is referring to the HyperTransport speed (the bus between the CPU and motherboard chipset): [http://www.hardwaresecrets.com/everything-you-need-to-know-about-the-hypertransport-bus/](http://www.hardwaresecrets.com/everything-you-need-to-know-about-the-hypertransport-bus/)

---

### Post by daniell59 on 2017-02-13
> **Temüjin said:**
> We're getting way outside the scope of your original question.



Sort of. [https://en.wikipedia.org/wiki/Performance_Rating](https://en.wikipedia.org/wiki/Performance_Rating)



This is referring to the HyperTransport speed (the bus between the CPU and motherboard chipset): [http://www.hardwaresecrets.com/everything-you-need-to-know-about-the-hypertransport-bus/](http://www.hardwaresecrets.com/everything-you-need-to-know-about-the-hypertransport-bus/)

Thank you for all of your assistance. It is much clearer now. In the future I will try to stay more on topic.

---

### Post by mörgæs on 2017-02-13
In post 4 Xubuntu was recommended. It's good advice for hardware of this age. 

I doubt Ubuntu will run well even with more memory.

Wait a day or two and do a fresh install of X/Lubuntu 16.04.2, and after that you can decide if more memory is needed.

---

### Post by poorguy on 2017-02-13
[URL="http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%204400+%20-%20ADA4400DAA6CD%20(ADA4400CDBOX).html"][COLOR=#000000]This is probably not the exact processor but it may give you an idea of what the numbers represent.[/COLOR]

[http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%204400+%20-%20ADO4400IAA5DD%20%28ADO4400DDBOX%29.html](http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%204400+%20-%20ADO4400IAA5DD%20%28ADO4400DDBOX%29.html)

[COLOR=#000000]More memory bigger workbench for whatever you are running it never hurts to add more memory.

[/COLOR]

[/URL]

---

