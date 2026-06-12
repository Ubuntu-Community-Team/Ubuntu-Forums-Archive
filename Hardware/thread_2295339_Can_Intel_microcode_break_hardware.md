---
title: "Can Intel microcode break hardware?"
date: 2015-09-17
forum: Hardware
---

### Post by flix3 on 2015-09-17
I had it installed. Then I changed mobo and Intel processor. Booted into Ubuntu. All Ok. I restarted on shutdown. Now my PC is completely dead. No power, no leds, nothing at all. Hope it's the mobo, because it's less expensive; but how can I be sure of this?

Do you think that the microcode can be the culprit?

---

### Post by lisati on 2015-09-17
Not sure what you mean by microcode, the word can mean different things to different people and according to context. Are you referring to BIOS/UEFI/equivalent?

---

### Post by flix3 on 2015-09-17
I mean the proprietary driver that can be installed in Ubuntu.

---

### Post by weatherman2 on 2015-09-17
I don't see how this driver could cause your motherboard to fail.   Assuming you have checked all of your connections, it's almost certainly either the power supply or the motherboard.  These things fail commonly on desktop PCs.  Inspect the motherboard for bulging capacitors.  For examples, search for web images of "blown caps."

---

### Post by grahammechanical on 2015-09-17
I used Additional Drivers to install the Intel microcode months ago and it has not done any damage to my machine. The purpose of this microcode is to change the functioning of the Intel CPU without the need to flash the BIOS. The microcode driver is loaded during the loading process of Linux/Ubuntu and it has to be loaded every time the machine is started. So, If the machine is not getting as far as starting to load Linux, then I do not think it could be this microcode.

[https://downloadcenter.intel.com/download/24661/Linux-Processor-Microcode-Data-File](https://downloadcenter.intel.com/download/24661/Linux-Processor-Microcode-Data-File)

Mind you, I do think that it is a good idea to disable this driver if we are going to change the CPU. Also to revert to using an open source video driver if we are going to change graphic cards. Is your new CPU in the list of CPUs in the Intel link?

Regards.

---

### Post by tgalati4 on 2015-09-18
Try a different power supply.  It's possible that unfiltered, high-frequency noise from a failing power supply has killed your motherboard.  Your CPU is probably OK.  Frustrating, but it happens.  Unless you have an oscilloscope to examine the output of your PSU, find another one (preferable a new one). 

When building a system with a new motherboard and CPU, it's generally a good idea to put a new PSU in it, because the PSU is the one thing that can quickly kill a motherboard.

It's unlikely that any driver would kill a motherboard or CPU.  In rare cases has installing Linux caused an unrecoverable Secure Boot issue.

---

### Post by flix3 on 2015-09-18
Ok. Thank you all.

So I suppose my PSU have broken my motherboard on Ubuntu restart.
BTW: the PSU dtil works in anothrr PC.

Hope it'not the CPU.

The main probem is that I've no chance of knowing which component (motherboard, cpu or psu) is broken.

---

### Post by tgalati4 on 2015-09-18
Yes, that is true.  Troubleshooting this type of problem is difficult.  I've never seen a blown Intel CPU.  I've seen several blown motherboards and even more blown PSU's.  It's possible that the PSU works in another system that draws less current.  When booting, the PSU needs to supply peak current and voltage drops as a result.  Some motherboards won't boot if the voltage is not up to specification.

What is the motherboard model?  What is the CPU model?  What version of Ubuntu did you install?

---

### Post by flix3 on 2015-09-18
Gigabyte H81M-H.
i5 4590

Today I've taken my mobo back to the shop with my processor and RAM; they tasted it and replaced my mobo for free. They say that a cpu failue would still allow its fan to move.

I'vee bought a Corsair PSU. Hope it workz better than mychaper one.

Tomorrow I'll test my system (but I'm still afraid to boointo Ubuntu 15.04 on my HD if the hardware is OK). I'll probably boot using an Ubuntu live CD.

Is there a way to disable proprietary drivers from a live cd to my HD?

---

### Post by tgalati4 on 2015-09-18
I would perform a fresh install.  There is no way to cleanly remove the proprietary drivers without booting the disk.  The drivers are linked into the kernel, so you can't just delete them.  You have to remove them using *synaptic* or *apt-get * and then immediately install the open source drivers.

---

### Post by flix3 on 2015-09-19
Ok.

Just a question: when you shut down your PC through the switch on your PSU and then you press that switch again, does your system soon power on without pressing the power switch on the case ?

I think this is an odd behavior: it happens even if I remove all the front panel connectors from the motherboard and use a screwdriver on the pins as a case power button.

It seems like the system is always power on. That may cause damage on restart. What do you think ?

---

### Post by tgalati4 on 2015-09-19
Most power supplies have a 5VDC line that keeps the motherboard powered during Sleep.  If there is a short in the motherboard, then this 5VDC can feed back into the ground and cause the PSU to wake and provide power to all the power pins and indeed wake your motherboard.  Sometimes the power-on transistors on the motherboard crap out and you have to use the green-wire-to-black shorting method to get the motherboard to boot.  I have had a couple of computers behave this way, but they were older and became servers, so they were always on anyways.

In BIOS, you can change the behavior of the power button--shut down immediately, hold-for-4-seconds-to-power-down, or sleep.  Because the motherboard is always powered with 5VDC, poking around while plugged in can cause a short and break the power-on circuitry.

---

### Post by flix3 on 2015-09-21
Thank you for your supportNow I'm experiencing stability problems.Hope I'll find out the cause (RAM,RAMslot or cpu).Nothing seems easy in this system upgrade!

---

### Post by flix3 on 2015-09-25
OK now my system seems to be stable  :p.

However I had to remove one of the two RAM modules (4 + 4 Gb Corsair Vengeance 1600 MHz), otherwise Ubuntu does not boot and the system hangs (usually soon after the bios screen, but once I managed to have an error message saying something about "kernel sync error").

The weird thing about this I once managed to perform a memtest and all the RAM seemed OK (although my system was detected as i7 instead of i5 inside memtest).

So I don't know what to think:
1 -> Is the RAM module broken (it's new!)
2 -> Can it be the RAM slot on the motherboard ?
3 -> Is there something I can do in the bios to "save" the RAM module?

Please help ](*,)!

P.S. I wasted some time because of the **nomodeset** flag missing in **grub** after the **NVIDIA** driver installation (I hope that this mod will be included soon as a post installation step): 
[URL="http://askubuntu.com/questions/140640/nvidia-drivers-and-kernel-update-problems-nomodeset"]http://askubuntu.com/questions/140640/nvidia-drivers-and-kernel-update-problems-nomodeset 

[/URL]

---

### Post by weatherman2 on 2015-09-25
Try each module in each RAM slot and run Memtest each time.  Let it run for just a few minutes in each combination, and if you find no errors, try running it longer.

If a RAM module is truly bad - that is, one with identical specs works perfectly but the other one fails, then no, you cannot "save" it but it may still be under warranty and you may be able to RMA it and get a free replacement.  Some RAM comes with a lifetime warranty.

If both RAM sticks work perfectly one at a time in each slot, then perhaps your motherboard has compatibility issues with so much RAM.  Have you tried updating the BIOS (or EFI firmware)?

---

### Post by tgalati4 on 2015-09-25
Understand that slight timing and voltage differences between RAM sticks can cause the entire RAM grouping to fail.  Sometimes the memory controller (Southbridge chip) can't handle the RAM density when fully populated or handle the CAS timing of a fully-populated board.  So, you can try reducing CAS timing or reducing front side bus speed and see if stability returns.

Try bumping up RAM voltage if your BIOS allows.

---

### Post by flix3 on 2015-09-26
This is really driving me mad :(!

From my tests it seems like one of my slots needs some "warming time" to work properly.
This is based upon the following considerations:

Hp) Currently I've got what I call **a good RAM module** and **a good RAM slot**, since with these the system is stable at every BIOS settings.


1) I tested just replacing my "good RAM module" with the other on the same slot: Ubuntu did not boot, with various errors (once I had: "Uncompression error. --system halted"). I thought: easy: the module is corrupted. But please read further:
2) Every time I perform a complete memtest on both modules together (the good one in the good slot), no  error is found. Tested at both 1333 Mhz and 1600 Mhz (the latter is  called Extreme Memory Profile in my BIOS). This may be caused by the  fact that th RAM warms up during memtest...
3) With both modules together the system usually crashes only while Ubuntu is loading. At the present moment I'm writing this post with both modules present (I set them at 1333) and the system is not crashing (well, to be sure I probably need more time...).

So basically I think I have one block that needs some kind of warming.[URL="http://ubuntuforums.org/member.php?u=241895"][COLOR=#000000]
[/COLOR][/URL]

---

### Post by tgalati4 on 2015-09-27
Get a different set of RAM sticks from a different manufacturer.  Try again with your testing.  If you have a bad slot, then get a new motherboard.  If the new RAM works use them.  There is no warming period--intermittent behavior is not reliable and not acceptable in a computer running linux.  You need perfect hardware because linux expects perfect hardware.

---

### Post by flix3 on 2015-09-28
Yes, it's probably the module that is bad. In fact now I can run the good module alone in the other slot without problems.
However before replacing it, I want to understand why memtest does not report errors: I've just downloaded memtest86+ v.5.01 and memtest86 v.6 and burned their .iso images to 2 CD-R: they should both support my system.

When I have time, I'll test the whole of my RAM (or maybe just the broken module?) with these new versions and see.

---

### Post by flix3 on 2015-09-29
Bad news for me again :(... but I'm getting used now...

Tested my modules nearly 10 times (and using both memory test programs): no RAM error detected, but a couple of crashes while memtest was running (especially when using the option that enables all the CPU cores together).

I've noticed that the crashes occurred when the CPU temperature was > 65° C.

So I guess I can have:

1) RAM problems that are undetectable by any memory tester (and I guess that the shop won't replace my modules for free because of that).
2) additional CPU heating problems.

I'm fed up with all these problems. For the time being, I think I'll stick to my stable configuration with 4 GB and pretend to be happy :rolleyes:. 


P.S. On my old motherboard I've got a bigger CPU cooler with a bigger fan (it was used to cool a Core Duo Quad: it was mounted on a kind of "cross" on the other part of the motherboard). Do you think that I can/must replace the default cooler/fan of my i5 with the old one (when I asked in the shop they told me not to do it) ?

P.S.2. Thank you all again for your support.

---

### Post by tgalati4 on 2015-09-29
I don't what the i5 CPU looks like, but if the old heat sink fits properly with 7 lbs of pressure, then you should be OK.  If the CPU is thinner, then the heat sink might not fit tightly enough to provide good heat transfer.

If your RAM tests out but you get crashes, then the soldering on the RAM slots could be bad so you get intermittent behavior.  I've seen this behavior before.  I would get a new motherboard and reduce the frustration level.

---

### Post by flix3 on 2015-09-30
> **tgalati4 said:**
> I don't what the i5 CPU looks like, but if the old heat sink fits properly with 7 lbs of pressure, then you should be OK.  If the CPU is thinner, then the heat sink might not fit tightly enough to provide good heat transfer.Yes, I suppose the new CPU is thinner... for sure it seems smaller.

> **tgalati4 said:**
> If your RAM tests out but you get crashes, then the soldering on the RAM slots could be bad so you get intermittent behavior.  I've seen this behavior before.  I would get a new motherboard and reduce the frustration level. Well, actually I've already replaced the motherboard once... this one should be OK (well, with the good RAM module it works, regardless the slot I use).

However I think it's better to close this thread now, thanks again for your support.

So the answer to the original question "Can Intel microcode break hardware?" is probably: No, Intel microcode is probably not the culprit in my case.

---

