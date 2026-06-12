---
title: "Computer only uses 3.5GB out of 4GB of RAM"
date: 2012-01-25
forum: Hardware
---

### Post by N00b-un-2 on 2012-01-25
I recently acquired an older computer, a Dell Optiplex 320 Desktop (not the mini tower).  I got it for practically nothing so I decided to spend the extra cash I had on putting a few upgrades into it, primarily a larger hard drive and more RAM.
A little bit about the computer, it has a 3.0Ghz P4 531 processor and uses ATI 200 Xpress chipset.  I just bought a 4GB DDR2 RAM upgrade and installed it and it boots up fine.  Overall performance has increased dramatically from the memory boost, but I've discovered that the computer is not using all of it's RAM.
At first I had installed Ubuntu 10.04 x86 and found that it was only addressing 3.5GB of the 4GB, so naturally I assumed that the limitation was from the 32 bit OS.  I installed the PAE kernel, but there was no change.  The computer is still using only 3.5 GB of RAM.
I just installed Ubuntu 10.04 x86_64, and the computer still reports only 3.5GB of RAM.
Out of curiosity I booted into the BIOS to see if there were any settings I could mess with.  The BIOS on this Dell is pretty limited, but I found that even in BIOS the computer reports that 2 sticks of 2GB DDR2 are installed in DIMMs 1 and 3 (there is no 2, I'm assuming it's used by the onboard graphics as dedicated VRAM), but the Total Memory says "3.5 GB".

I decided to update the BIOS to the latest version available (Dell BIOS 1.1.12 released Aug '09) to see if that would make a difference.  After updating I booted back into the new BIOS only to find the exact same thing, 2x2GB of DDR2 installed, only 3.5GB of it in use.

Not that 512MB of RAM is a huge deal, I'm just wondering if there is anything I can do to enable it on my computer.

---

### Post by wolfen69 on 2012-01-25
I have 4gb of ram on my laptop, and ubuntu only sees 3.8gb. I assume in your case, the integrated video is using an extra 300mb. Probably nothing you can do about it.

---

### Post by N00b-un-2 on 2012-01-25
It is using 300MB of RAM as shared memory for video.  In Ubuntu system monitor, it actually reports 3.2GB of memory.  The BIOS reports 3.5GB of RAM available.  Is my computer's board limited to 3.5GB?

---

### Post by xyzzyman on 2012-01-26
[http://en.community.dell.com/support-forums/desktop/f/3514/p/19243086/19374153.aspx](http://en.community.dell.com/support-forums/desktop/f/3514/p/19243086/19374153.aspx)

Look at the last response especially.

---

### Post by madvinegar on 2012-01-26
First of all, for all I know, you "cannot" install 64bit OS in all systems.

64bit OS work with processors like **core _2_ duo** and above. In a P4 processor, you can only install 32bit systems. And when I say that "you can only install 32bit system" I mean that it will work **properly**.

So, even if you have installed the 64bit OS (which theoretically can handle the 4gb of ram) your processor cannot handle the 64bit OS.

It is like a chain. First the processor, then the 64bit system and then the 4gb of ram (or more).

On the other hand, I would be very happy in your case considering that your PC actually sees 3,5gb of ram with a P4 processor! I was expecting that it could only read up to 3gb! So, you should be happy!

---

### Post by MoreOrLess on 2012-01-26
> **madvinegar said:**
> 64bit OS work with processors like core 2 duo and above. In a P4 processor, you can only install 32bit systems
False. Later Pentium 4's came with 64-bit support. If the model number is 5x1 (like the OP's 531) or 6x1, it supports 64-bit.

---

### Post by N00b-un-2 on 2012-01-26
> **madvinegar said:**
> First of all, for all I know, you "cannot" install 64bit OS in all systems.

64bit OS work with processors like **core _2_ duo** and above. In a P4 processor, you can only install 32bit systems. And when I say that "you can only install 32bit system" I mean that it will work **properly**.

So, even if you have installed the 64bit OS (which theoretically can handle the 4gb of ram) your processor cannot handle the 64bit OS.

It is like a chain. First the processor, then the 64bit system and then the 4gb of ram (or more).

On the other hand, I would be very happy in your case considering that your PC actually sees 3,5gb of ram with a P4 processor! I was expecting that it could only read up to 3gb! So, you should be happy!

Not to argue with you, but the P4 chip does in fact have EM64T instruction set capability.  Not only that but running the 64 bit Ubuntu actually cleared up an issue with video artifacting that I was experiencing on 32bit after the ram upgrade.  So you are simply incorrect.

---

### Post by N00b-un-2 on 2012-01-26
Proof of 64 bit capability
[IMG]http://img560.imageshack.us/img560/5569/screenshotia.png[/IMG]
and here is the CPU info from CPU-Z on the Windows side
```

CPU-Z TXT Report

-------------------------------------------------------------------------



Binaries

-------------------------------------------------------------------------



CPU-Z version			1.59



Processors

-------------------------------------------------------------------------



Number of processors		1

Number of threads		2



APICs

-------------------------------------------------------------------------



Processor 0	

	-- Core 0	

		-- Thread 0	0

		-- Thread 1	1



Processors Information

-------------------------------------------------------------------------



Processor 1			ID = 0

	Number of cores		1 (max 1)

	Number of threads	2 (max 2)

	Name			Intel Pentium 4 531

	Codename		Prescott

	Specification		Intel(R) Pentium(R) 4 CPU 3.00GHz

	Package (platform ID)	Socket 775 LGA (0x4)

	CPUID			F.4.9

	Extended CPUID		F.4

	Core Stepping		G1

	Technology		90 nm

	Core Speed		3000.2 MHz

	Multiplier x FSB	15.0 x 200.0 MHz

	Rated Bus speed		800.1 MHz

	Stock frequency		3000 MHz

	Instructions sets	MMX, SSE, SSE2, SSE3, EM64T

	L1 Data cache		16 KBytes, 8-way set associative, 64-byte line size

	Trace cache		12 Kuops, 8-way set associative

	L2 cache		1024 KBytes, 8-way set associative, 64-byte line size

	FID/VID Control		no
```
So as you can see, your assumption that the P4 chip is not 64bit capable is incorrect.  Not only is it 64bit capable, but the computer runs far better with a 64 bit OS which alleviates the graphics artifacting issues and corrects an error at boot that requires "nomodeset" to be added to GRUB entries in order to boot.  Please for the sake of others on the forum do some research before making such claims.

So... back to the original issue, why is my computer not addressing all the RAM I'm feeding it?

---

### Post by N00b-un-2 on 2012-01-26
> **xyzzyman said:**
> [http://en.community.dell.com/support-forums/desktop/f/3514/p/19243086/19374153.aspx](http://en.community.dell.com/support-forums/desktop/f/3514/p/19243086/19374153.aspx)

Look at the last response especially.

I had already read that post.  However, that is a completely separate issue.  The problem there is a limitation of the power supply, where if a PCI-e graphics card is installed there is not enough power to address a second DIMM of RAM.  I'm using onboard graphics so this is not an issue.

As I stated in a previous post my computer is in fact allocating 300 MB of RAM to the video card as shared VRAM.  This is 300 out of the 3500MB of total RAM.  So in essence,  I paid for 4 GB of RAM and I'm getting 3.2.
Windows reports the exact same thing on both 32bit and 64bit Windows 7, so it appears to be a hardware limitation at this point. My assumption is that this is a limitation of the board itself so I'm trying to see where the bottleneck is and whether or not it can be addressed.  As mentioned before, I did already update the BIOS to the most recent version, Dell BIOS rev 1.1.12 to no avail.

---

### Post by madvinegar on 2012-01-26
> **N00b-un-2 said:**
> Please for the sake of others on the forum do some research before making such claims.


Actually I have done some research on the above matter as I wanted myself to install the 64bit OS, but the info I have found was that the processor has to be core 2 duo and above for the 64bit OS to run properly.

Imagine that I have a Dual Core processor and I was told in various forums not to install the 64bit OS and that I am better suited with the 32bit one.

Nevertheless, at least you have considerable proof about it, so it's fine by me.

Now you have put to my head ideas to try the 64bit OS myself. Will it run properly on a Dual Core System...???

---

### Post by N00b-un-2 on 2012-01-26
There is no right or wrong answer as far as 32bit vs 64bit.  If you have 4 or more GB or RAM it's recommended that you install 64 bit.  That being said, 32 bit Linux with a PAE kernel (assuming your CPU architecture supports physical address extension instruction set) will in fact address 4 GB or more RAM.
in many cases hardware support is better on 32 bit Linux, but unlike 32 bit windows, 32 bit hardware drivers can be forced to work on 64 bit Linux by installing ia32-libs and any dependencies the drivers may have, and then installing any packages using the --force-architecture or --force-all argument.  Case in point, I have two printers at my house a Lexmark X1150 and a Brother MFC-490CW.  Both have 32 bit Linux drivers, but no 64 bit support.  I have both printers fully functioning on 64 bit Ubuntu.

Virtually all CPUs now are 64 bit capable.  Even my netbook Intel Atom N450 is 64 bit capable.

The benefits of using 64 bit typically include moderate to substantial increase in speed of CPU intensive operations such as video editing, compiling source etc.  The traditional reason for people upgrading to 64 bit was to bypass the 4GB RAM cap on 32 bit, but as I said this is negated by the PAE kernel.  If you're not very familiar with how Linux works and aren't afraid of using the terminal then go for 64 bit.  That being said,the reason why Ubuntu recommends 32 bit is because of hardware support.

---

### Post by madvinegar on 2012-01-26
> **N00b-un-2 said:**
> There is no right or wrong answer as far as 32bit vs 64bit.  If you have 4 or more GB or RAM it's recommended that you install 64 bit.  That being said, 32 bit Linux with a PAE kernel (assuming your CPU architecture supports physical address extension instruction set) will in fact address 4 GB or more RAM.
in many cases hardware support is better on 32 bit Linux, but unlike 32 bit windows, 32 bit hardware drivers can be forced to work on 64 bit Linux by installing ia32-libs and any dependencies the drivers may have, and then installing any packages using the --force-architecture or --force-all argument.  Case in point, I have two printers at my house a Lexmark X1150 and a Brother MFC-490CW.  Both have 32 bit Linux drivers, but no 64 bit support.  I have both printers fully functioning on 64 bit Ubuntu.

Virtually all CPUs now are 64 bit capable.  Even my netbook Intel Atom N450 is 64 bit capable.

The benefits of using 64 bit typically include moderate to substantial increase in speed of CPU intensive operations such as video editing, compiling source etc.  The traditional reason for people upgrading to 64 bit was to bypass the 4GB RAM cap on 32 bit, but as I said this is negated by the PAE kernel.  If you're not very familiar with how Linux works and aren't afraid of using the terminal then go for 64 bit.  That being said,the reason why Ubuntu recommends 32 bit is because of hardware support.

Many thanks for your above reply.
Just for the record, I have installed 4gb of ram in my laptop. The manufacturer says that maximum 2gb is acceptable. (Genuine Intel CPU T2250 1.73GHz)
The 32bit linux OS I have installed only reads 3gb (2.9gb to be exact is shown in system monitor).
To be honest, I do not think that even if I install 64bit OS, the laptop will manage to read more than 3gb.
Plus the fact that you mentioned that 32bit is better supported by hardware. So I stayed with 32bit OS...
How can I see exactly how much ram is being seen?

In any case, thanks again for your advices.

---

### Post by wolfen69 on 2012-01-26
> **madvinegar said:**
> 
Plus the fact that you mentioned that 32bit is better supported by hardware.
99.999% of hardware supported in 32bit is supported in 64bit. Only the most esoteric of hardware will not have a 64bit driver. But as someone said, you can use the 32bit driver on 64. 64bit is more than ready for primetime, as evidenced by canonical's decision to make 64bit ubuntu the default standard download beginning in 3 months.
> How can I see exactly how much ram is being seen?
*System Monitor* can tell you that. Or 
```
top
```
in the terminal.

---

### Post by MoreOrLess on 2012-01-26
See if there are any memory remapping or iommu settings in the bios.

---

### Post by xyzzyman on 2012-01-26
> **N00b-un-2 said:**
> I had already read that post.  However, that is a completely separate issue.  The problem there is a limitation of the power supply, where if a PCI-e graphics card is installed there is not enough power to address a second DIMM of RAM.  I'm using onboard graphics so this is not an issue.

As I stated in a previous post my computer is in fact allocating 300 MB of RAM to the video card as shared VRAM.  This is 300 out of the 3500MB of total RAM.  So in essence,  I paid for 4 GB of RAM and I'm getting 3.2.
Windows reports the exact same thing on both 32bit and 64bit Windows 7, so it appears to be a hardware limitation at this point. My assumption is that this is a limitation of the board itself so I'm trying to see where the bottleneck is and whether or not it can be addressed.  As mentioned before, I did already update the BIOS to the most recent version, Dell BIOS rev 1.1.12 to no avail.

Dell only sold the system originally as supporting 2GB. People have reported luck installing 4GB, but if you have access to Dell's support site for authorized warranty workers they are still requesting to only recommend up to 2GB. It's a known issue with the board itself on over 2GB.

---

### Post by N00b-un-2 on 2012-01-26
If 3.5GB is the max I can get out of my system, then it was worth $40 for the upgrade.  FWIW I just bought a Core2Duo E4300 CPU which I will swap when I receive it in a few days.  I did a ton of research to make sure that dual core was even possible (which I'm still skeptical about) but my research indicated that the E4300, a 1.8Ghz first generation Core2Duo CPU is the best CPU I can use on the Optiplex board.  CPU upgrade reports have been hit or miss, many simply failing to post.  The E4300 is a non hyperthreading CPU so performance increase isn't going to be dramatic but will certainly help for CPU intensive applications like video editing or compiling.  I'm hoping that >>just maybe<< the CPU upgrade will enable use of the rest of my RAM, but I'm doubtful.

---

### Post by N00b-un-2 on 2012-01-26
> **madvinegar said:**
> Many thanks for your above reply.
Just for the record, I have installed 4gb of ram in my laptop. The manufacturer says that maximum 2gb is acceptable. (Genuine Intel CPU T2250 1.73GHz)
The 32bit linux OS I have installed only reads 3gb (2.9gb to be exact is shown in system monitor).
To be honest, I do not think that even if I install 64bit OS, the laptop will manage to read more than 3gb.
Plus the fact that you mentioned that 32bit is better supported by hardware. So I stayed with 32bit OS...
How can I see exactly how much ram is being seen?

In any case, thanks again for your advices.

Try the PAE kernel.  Instructions to install PAE are found here [https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

For RAM type 
free -m
in terminal

---

### Post by Starks on 2012-01-26
The RAM limitations of 32-bit also include the RAM of the video card.

System RAM + VRAM cannot exceed 3.5GB.

Not sure how PAE factors into it.

---

### Post by mcduck on 2012-01-26
> **Starks said:**
> The RAM limitations of 32-bit also include the RAM of the video card.

System RAM + VRAM cannot exceed 3.5GB.

Not sure how PAE factors into it.

...and in addition to video memory, it also includes all the hardware addresses the system needs to use. Which is why a 32-bit system will never be able to use the full 4GB of RAM, and instead depending on the hardware only addresses something bit over 3GB.

(and also when talking about the memory addresses used by graphics card, this actually has nothing to do with GPU using shared memory or not. Even if you have dedicated graphics memory, it's still taking some of the available memory addresses. So the more your graphics card has dedicated memory, the less there are memory addresses available for RAM).

Using a PAE kernel of course solves the problem, but in pretty much every case going for a proper 64-bit system, if possible, would give even better results. SO I'd recommend PAE as a solution only if you are using 32-bit hardware, or can't make a fresh install of a 64-bit system right now.

---

### Post by madvinegar on 2012-01-26
> **N00b-un-2 said:**
> Try the PAE kernel.  Instructions to install PAE are found here [https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

For RAM type 
free -m
in terminal


As I have seen in synaptics packages, (and from ```
grep --color=always -i PAE /proc/cpuinfo
```) it is already enabled.

---

### Post by N00b-un-2 on 2012-01-26
by default if you have 4GB or more of RAM, the Ubiquity installer should automatically configure a fresh install to use the PAE kernel.  But it's been said here already, in virtually all cases installing 64 bit OS will result in better performance over 32 bit, even with PAE.

btw, cpuinfo will only display your CPU's capabilities not what kernel you are using.  Your kernel is uname -a

---

### Post by N00b-un-2 on 2012-02-01
```
larissa@larissa-ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping	: 2
cpu MHz		: 1800.083
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3600.16
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping	: 2
cpu MHz		: 1800.083
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3600.18
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

larissa@larissa-ubuntu:~$ 

```

Just wanted to boast a little bit!  I'd read on some Dell forums that the Optiplex 320' 651OMH motherboard is simply not dual core capable (certainly not officially supported as such by Dell).  the E4300 Core2Duo runs just fine on this system and has given the computer a noticeable increase in performance and responsiveness.  I'm pretty sure that the computer should support the E4700 cpu as well which is 800MHz faster.  tempted to buy one.

---

### Post by xyzzyman on 2012-02-01
> **N00b-un-2 said:**
> ```
larissa@larissa-ubuntu:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping	: 2
cpu MHz		: 1800.083
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3600.16
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping	: 2
cpu MHz		: 1800.083
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
bogomips	: 3600.18
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

larissa@larissa-ubuntu:~$ 

```

Just wanted to boast a little bit!  I'd read on some Dell forums that the Optiplex 320' 651OMH motherboard is simply not dual core capable (certainly not officially supported as such by Dell).  the E4300 Core2Duo runs just fine on this system and has given the computer a noticeable increase in performance and responsiveness.  I'm pretty sure that the computer should support the E4700 cpu as well which is 800MHz faster.  tempted to buy one.

They sold those systems with dual-core CPU's. You could buy them with Pentium D's which were dual-core or actual Core 2 Duo's if you called and asked and were buying in lots.

---

### Post by N00b-un-2 on 2012-02-01
They sold the later model Micro ATX mini tower Optiplex 320 with Core2Duo.  However, they are not at all the same product.  First and foremost the Desktop mid tower is BTX form factor.  Even after a BIOS update from Dell's support site and then upgrading the CPU to the C2D, the BIOS splash screen has a big Pentium 4 logo in the bottom right.  So I'm pretty sure it's safe to say that the 320 tower with the OMH651 motherboard never came with Core2Duo.  Otherwise why would the P4 logo be hard coded into the BIOS?

---

### Post by xyzzyman on 2012-02-01
> **N00b-un-2 said:**
> They sold the later model Micro ATX mini tower Optiplex 320 with Core2Duo.  However, they are not at all the same product.  First and foremost the Desktop mid tower is BTX form factor.  Even after a BIOS update from Dell's support site and then upgrading the CPU to the C2D, the BIOS splash screen has a big Pentium 4 logo in the bottom right.  So I'm pretty sure it's safe to say that the 320 tower with the OMH651 motherboard never came with Core2Duo.  Otherwise why would the P4 logo be hard coded into the BIOS?

That happened on alot. When I was doing alot of onsite warranty work for Dell I'd have customers confused. I forget which Dimension model had the Celeron D logo but people would be suprised to find out they had better processors... Which made no sense because they had to have customer ordered that upgrade.

It also worked in reverse. I was in an office and somehow they had gotten Dimension 4700's ordered with Celerons. I pointed out that even with the 2GB of RAM that's why their application was lagging, and they thought they had been running P4's with hyper-threading as that's the logo they saw at boot. Go figure. Who ordered Dimensions for an office setting is beyond me anyways.

---

### Post by madvinegar on 2012-02-02
Just on a helpful note regarding our previous discussions, I found out that you can easily check if your system is capable of running 64bit OS by writing the following command in terminal:

```
sudo lshw -C Processor | grep width
```


The width of mine has proven to be 32 bit, and even with the installation of the pae kernel, the system could not use more than 3gb of ram (3086MiB to be exact).

---

