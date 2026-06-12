---
title: "RAM all installed not visible"
date: 2011-08-09
forum: Hardware
---

### Post by DNAcombo on 2011-08-09
Hi,
I have ubuntu 11.04, 64bit, installed 24GB of ram and can only use 16GB. How I can actually use all of my 24GB?
I've read a bit about this issue and (in 2010 or beginning of this year) it seems like people had a similar problem with 4GB installed and seeing only 3GB. It was then question of installing a 64bits version of ubuntu or a PAE kernel. It is obviously not the problem here.
Is ubuntu able to handle 24GB without wasting 8GB for allocation or whatever it is required to do?

Any advice will be appreciated.
Thanks!


```
uname -a
Linux Oszilla 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
``````
free -m
total       used       free     shared    buffers     cached
Mem:         16079      12714       3364          0        173       9220
-/+ buffers/cache:       3320      12758
Swap:        19529         56      19473
``````
sudo lshw | sed -n '/*-memory/,/*-pci/p' | head -n -1
*-memory             
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 24GiB
        *-bank:0
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: M391B5273CH0-CH9
             vendor: Samsung
             physical id: 0
             serial: 8785D3C2
             slot: DIMM 1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: M391B5273CH0-CH9
             vendor: Samsung
             physical id: 1
             serial: 8785D3B1
             slot: DIMM 2
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: M391B5273CH0-CH9
             vendor: Samsung
             physical id: 2
             serial: 8785D3C3
             slot: DIMM 3
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: M391B5273CH0-CH9
             vendor: Samsung
             physical id: 3
             serial: 8785D3BD
             slot: DIMM 4
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:4
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: M391B5273CH0-CH9
             vendor: Samsung
             physical id: 4
             serial: 8785D3BF
             slot: DIMM 5
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:5
             description: DIMM DDR3 1333 MHz (0.8 ns)
             product: M391B5273CH0-CH9
             vendor: Samsung
             physical id: 5
             serial: 8785D3BE
             slot: DIMM 6
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
```

---

### Post by jerrrys on 2011-08-09
lshw is seeing the hardware, but can you use it?  you didn't exceed the max ram allowed on your box?

---

### Post by DNAcombo on 2011-08-10
Hi,
Well, that's the point, I cannot use 8GB of the 24GB that are installed and recognized by lshw.
I don't know that I exceeded the max amount of ram allowed. It's a fairly recent machine, the chips are of the right format, installed and seem to function.
Actually, we had 12GB before (6 bars of 2GB) and it was already (if I remember correctly) showing only 8GB.
My impression is that for some reason, the system is using a fourth of the ram to address or something like that. That sounds just a bit excessive to me. Isn't it?

Anyone had a similar issue before?

Thanks!

---

### Post by grahammechanical on 2011-08-10
Hi

This is just a wild guess. Do you have a dedicated graphics adapter or is some of the system RAM used as video RAM? Just one more thing to tick off. 

Also, does the BIOS show 24GB? Can you make the POST messages visible and watch the BIOS test the RAM and show how much is there?

Regards.

---

### Post by DNAcombo on 2011-08-10
Alright, today while starting up, it says there's a memory error on DIMM 2.
There are 6 slots in there. Is there any rule that would tell me which one is not working? Do I take away the chip that's 2 to the top or 2 to the bottom? Or 3, if it's counting from zero, which I think it is, if I trust what lshw returned earlier.

I'll keep looking into this. Anyone with experience with DELL Precision T3500 tower is welcome to give me some advice.

I'll come back with my solution later on.

Thanks.

---

### Post by trundlenut on 2011-08-10
Have a careful look at the motherboard, it is likely that at least one row will be identified, probably in very small text.

---

### Post by DNAcombo on 2011-08-12
I found DIMM 2. Unplugged it, replugged it, nothing changed.

Wanted to check if the problem came from the motherboard or from the memory chip. Switched the chips in DIMM 2 and DIMM 3. Now all work fine. The computer now displays 23.6GB useable. Problem solved.

Thanks for your assistance!

---

