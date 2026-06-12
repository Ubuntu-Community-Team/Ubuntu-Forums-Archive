---
title: "256 MB RAM Registers as 117 MB?"
date: 2010-03-10
forum: Hardware
---

### Post by eyehavenoi on 2010-03-10
Hello,

I'm running Ubuntu 9.10 an old machine that was previously running Windows 98.
It's an Intel 810 chipset. I just received two 256 MB RAM sticks that are both registering as 117.6 MB. With two of them in, it registers 243MB, strange because (117.6 x 2 = 235.2).

I swapped out one of the new sticks for an old 256 and the two are still registering as 243 total. I had initially thought one of the original sticks was bad.

At first I thought I might have a bad bus, but they each register as 117.6 on their own.

Any thoughts?

I'm trying using this pc as a server so the available RAM doesn't matter all too much. I'd just like to know what's causing this issue... thanks!

---

### Post by Fafler on 2010-03-11
The 810 chipsset reserves some some memory for the build in graphics. But it shouldn't be more than 8 or 16 mb.

I don't think Linux is able to exclude bad memory without having special parameters passed to the kernel. Have you run memtest86+?

---

### Post by cascade9 on 2010-03-11
You have a point Fafler. the i810 will be eating some memory, but the only way to know how much, for sure, would be to check the BIOS. 

If the sticks you are installing are double sided, its possible that the chipset is only reading 1/2 the stick (only 1 side not both).

---

### Post by PRC09 on 2010-03-11
Some older machines also have a limit on how much ram is allowed in each slot.You may check the original spec sheet and see if that is the case.

---

### Post by kerry_s on 2010-03-11
you need to check the max ram of the board. try putting only 1 of the 256mb rams in, i suspect 256mb is the max.

---

### Post by Fafler on 2010-03-11
The 810 maxes out at 768 mb. But the single/double side thing could be the issue here. If both modules are double sided, and the board only uses one side of each module, it's 128 mb - 117 mb = 11 mb reserved for graphics with one module and 256 - 243 = 13 mb. Add some better rounding of the numbers and this might just be it. How did you, by the way, get these number? From the BIOS or from inside Linux? Linux reserves some memory for special purposes that isn't displayer with tools like free. The laptop i'm sitting with right now has 512 mb installed, but free -m reports 496 mb as the total amount of memory.

---

### Post by cascade9 on 2010-03-11
I'm yet to see any i810 motherbaord that does more than 512MB. They could exist, I spose, I have seen i815s go to 786MB where they almost all topped out at 512MB. 

Aside from that, I agree. ;)

---

### Post by Fafler on 2010-03-11
Sorry, you're right. 512 is max according to the datasheet. It supports up to two double sided modules. If the board has 3 memory slots, only one module can be double sided, but i'm not sure whether the configuration is hardwired or detected on boot.

---

### Post by eyehavenoi on 2010-03-11
Here's my system monitor:
[IMG]http://img.photobucket.com/albums/v37/muted_orchestra/Screenshot.png[/IMG]

free -m:
```
             total       used       free     shared    buffers     cached
Mem:           243        239          3          0          4         42
-/+ buffers/cache:        193         50
Swap:          384        100        283
```The sticks in now are single-sided.
I have two double-sided sticks that are giving me the same results..

It's an 810L - according to the wiki, the capacity should be 512mb
Only two busses

Thanks for the replies!
Will run memtest86+

---

### Post by eyehavenoi on 2010-03-11
> **eyehavenoi said:**
> 
Will run memtest86+

Can I run memtest inside Ubuntu or do I need to boot into it?
I'm still pretty new at this.

If I put it on a usb drive and boot from that drive will that run it?

Thanks guys

---

### Post by eyehavenoi on 2010-03-11
I just restarted Ubuntu and realized I could load it from Grub.
My b. 8)

---

### Post by shazbut on 2010-03-11
As others have postulated, the i810 chipset can only handle up to 128Mbit DRAM chip density.  So if your 256MByte modules have only 8 chips, it means the chips are 256Mbit (8 bits/byte).  The only 256MByte module that will be fully recognised by the i810 is one which has 16 chips on board (ie 16 chips x 128Mbit x 8bits-per-byte = 256 MByte).

There used to be a good online resource for which densities were supported by the various chipsets, but the owner took it down and was looking to sell it.

---

### Post by eyehavenoi on 2010-03-12
> **shazbut said:**
> As others have postulated, the i810 chipset can only handle up to 128Mbit DRAM chip density.  So if your 256MByte modules have only 8 chips, it means the chips are 256Mbit (8 bits/byte).  The only 256MByte module that will be fully recognised by the i810 is one which has 16 chips on board (ie 16 chips x 128Mbit x 8bits-per-byte = 256 MByte).

Well, I have two sets of sticks. Both are 2x256
set1: 8 chip single sided
set2: 18 chip, 9 on each side. These sticks are a lot taller if that helps for any sort of identification.

Neither of the sets registers as 512. I just put in set2 and am running memtest86+.
Celeron 634.8Mhz
L1 Cache:  16K     5932 MB/s
L2 Cache: 128K    2479 MB/s
L3 Cache:     None
Memory: 255M     181 MB/s
Chipset: Intel i810

Unsure what I should be looking for...

---

### Post by shazbut on 2010-03-15
set1 are 8x256Mbit modules, so only half the available RAM of each module would be recognised by the chipset.

set2 sound like they are 128Mbit ECC RAM (16x128 + 2x128 for ECC). Problem might be that ECC RAM may not be supported by the i810 chipset.  Or also, like someone else mentioned, the board may only be able to utilise one double sided module.

---

