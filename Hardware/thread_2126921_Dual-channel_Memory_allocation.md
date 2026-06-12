---
title: "Dual-channel Memory allocation"
date: 2013-03-18
forum: Hardware
---

### Post by nibal on 2013-03-18
I have a dual boot 64x system with Windows 7 and Ubuntu 12.04.
I also have an ASRock motherboard with dual-channel memory bus and 2 GB on slot 1 & 2 GB on slot 3, for a total of 4 GB. This is verified by BIOS and CPU-Z utility from Windows (see attachement).
Additionally CPU-Z reports that Dual-channel works fine. However Ubuntu's 12.04 kernel recognizes only 2 GB :(:

```

~-> cat /proc/meminfo
MemTotal:      2041748 kB
MemFree:        790660 kB
Buffers:         50556 kB

~-> free
                           total       used       free     shared    buffers     cached
Mem:                     2041748    1239408     802340          0      51220     521320
-/+ buffers/cache:        666868    1374880
Swap:                    2103292          0    2103292


```

Dual-Channel memory PCs have been around since 2008. What gives?
I imagine that the packaged kernel is no good. Anyone knows what is
the package name for the kernel sources?

TIA,
Nikos

---

### Post by nibal on 2013-03-18
> **nibal said:**
> I have a dual boot 64x system with Windows 7 and Ubuntu 12.04.
I also have an ASRock motherboard with dual-channel memory bus and 2 GB on slot 1 & 2 GB on slot 3, for a total of 4 GB. This is verified by BIOS and CPU-Z utility from Windows (see attachement).
Additionally CPU-Z reports that Dual-channel works fine. However Ubuntu's 12.04 kernel recognizes only 2 GB :(:

```

~-> cat /proc/meminfo
MemTotal:      2041748 kB
MemFree:        790660 kB
Buffers:         50556 kB

~-> free
                           total       used       free     shared    buffers     cached
Mem:                     2041748    1239408     802340          0      51220     521320
-/+ buffers/cache:        666868    1374880
Swap:                    2103292          0    2103292


```

Dual-Channel memory PCs have been around since 2008. What gives?
I imagine that the packaged kernel is no good. Anyone knows what is
the package name for the kernel sources?

TIA,
Nikos

OOps! forgot the attachment.

---

### Post by nibal on 2013-03-18
> Dual-Channel memory PCs have been around since 2008. What gives?
> I imagine that the packaged kernel is no good. Anyone knows what is
> the package name for the kernel sources?

Actually, it should be fine. It seems that free and /proc report available memory for userspace programs. Windows 7 Task Manager, also reported 2 GB available physical memory, but also that 4 GB were installed. Further analysis in Windows showed that
a full 2 GB are being used by hardware and graphic cards. Actually my Nvidia card has 1 GB VRAM, but as far as the rest of the hardware goes, it could only be IDE and SATA drivers. VRAM is mapped to system RAM. However, that mapping is due to the NVidia driver, which is part of the kernel, as well as the SATA buses. Shouldn't these be part of the kernel memory and be reported as used by the kerenel?

Also:
```

~-> cat /proc/meminfo 
MemTotal:        2041748 kB
MemFree:          881472 kB
[...snip...]
DirectMap4k:      107968 kB
DirectMap2M:     1980416 kB

```

Anyone knows what is this huge DirectMap2M?

TIA,
Nikos

---

### Post by oldfred on 2013-03-18
My system just shows a small amount less than total RAM for me. I have 1.5GB.
DirectMap2M:     1505280 kB

What does this show and then you may want to test and/or remove clean and reinstall the bank not seen.
sudo lshw | grep -m 1 -A 25 "*-memory"

---

### Post by nibal on 2013-03-19
@oldfred:
> My system just shows a small amount less than total RAM for me. I have 1.5GB.
> DirectMap2M:     1505280 kB

Hmmm. Do you have 3 GB total SIMMs installed? 
I just installed another Dual-channel 4 GB for a total of 8 GB:

```

~-> sudo cat /proc/meminfo
MemTotal:        4040108 kB
MemFree:         2530356 kB
[..snip...]
DirectMap4k:      122304 kB
DirectMap2M:     4063232 kB

~-> free
                     total       used       free     shared    buffers     cached
Mem:               4040108    1443960    2596148          0      60268     717384
-/+ buffers/cache:  666308    3373800
Swap:              2103292          0    2103292

```

As you can see, and comparing with my initial post, missing 4 GB are not for kernelspace, but since it increased from 2 GB to 4 GB without adding anything else, it must be some proportional 50% memory reduction for buffers, caches, etc. Very poor reporting, since free lists all userspace buffers and are subtracted from total available reported RAM.

> sudo lshw | grep -m 1 -A 25 "*-memory"

Darn, I was looking for that command. Coming from a SuSe background i was looking for "hwinfo" and coudln't find it:

```

-> sudo lshw > out
-> cat out
 *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 2GiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
             size: 2GiB
             width: 64 bits
        *-bank:3
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
             size: 2GiB
             width: 64 bits

```

This single command solves the whole issue. :smile:  It is not a kernel problem, just a reporting problem. 50% of the total  installed memory is reserved for unknown reasons - not userspace buffers, kernelspace buffers maybe?

Thanks a lot,
Nikos

---

### Post by oldfred on 2013-03-19
That was my laptop with only 1.5GB RAM.
This is from my Desktop which has 4GB of RAM.
It does not make sense that you only see half?
I have used hwinfo, but think I had to install it.

```

fred@fred-Precise:~$ free
             total       used       free     shared    buffers     cached
Mem:       4048532    1310988    2737544          0     189316     496200
-/+ buffers/cache:     625472    3423060
Swap:      7268664          0    7268664

```
```
fred@fred-Precise:~$ cat /proc/meminfo
MemTotal:        4048532 kB
MemFree:         2737776 kB
Buffers:          189300 kB
Cached:           496176 kB
SwapCached:            0 kB
Active:           595104 kB
Inactive:         534100 kB
Active(anon):     444584 kB
Inactive(anon):     1184 kB
Active(file):     150520 kB
Inactive(file):   532916 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       7268664 kB
SwapFree:        7268664 kB
Dirty:                32 kB
Writeback:             0 kB
AnonPages:        443688 kB
Mapped:           116516 kB
Shmem:              2024 kB
Slab:              62896 kB
SReclaimable:      38660 kB
SUnreclaim:        24236 kB
KernelStack:        3264 kB
PageTables:        24312 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     9292928 kB
Committed_AS:    2572164 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      122068 kB
VmallocChunk:   34359601148 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       95104 kB
DirectMap2M:     4098048 kB
```

---

### Post by nibal on 2013-03-20
@oldfred:
> I have used hwinfo, but think I had to install it.

 Nice to know it is not an specific opensuse tool, although lshw covers it! ;-)

```

fred@fred-Precise:~$ free
                        total       used       free     shared    buffers     cached
    Mem:              4048532    1310988    2737544          0     189316     496200
   -/+ buffers/cache:  625472    3423060
    Swap:             7268664          0    7268664

```

  Very interesting. I am using Ubuntu 12.04 with the latest kernel. The result is verified by my Windows 7 installation. Going to task Manager -> Resource Monitor I find out that now it reserves for hardware 4 GB! Before it was reserving only 2 GB and the only thing I added was 4 GB of extra Dual-channel memory. (see attachment). So no matter what i do I loose 50% of my installed memory. It would be tempting to say that this is a BIOS feature, except that in Windows Resource Monitor, and in Ubuntu lshw detect and see the whole installed memory (8 GB) (see attachment) and besides what would BIOS need 4 GBs for?. I will pursue this also in the Windows forums, because i don't like paying double for the same amount of memory, and i have indications that this "reserved" memory is not released on demand, but instead I start swapping.

 Meanwhile, I am reopening the thread, since any feedback by Ubuntu is very welcome. This is the thread that doesn't want to die!:)

Thanks,
Nikos

---

### Post by Yellow Pasque on 2013-03-20
I've seen a few ASRock owners report missing RAM, and I'm still suspicous of the "X-fast RAM" feature not playing well with Linux and/or automatically grabbing RAM. [http://www.asrock.com/feature/xfast/xfastram/index.asp](http://www.asrock.com/feature/xfast/xfastram/index.asp)

In general, with missing RAM issues:
1. Make sure your BIOS is up-to-date
2. Look in BIOS for IOMMU or memory remapping options
3. Test with latest kernel (an Ubuntu 13.04 64-bit LiveUSB would be handy)
4. Check dmesg for details. I find this command helpful:
```
dmseg | grep e820
```

---

### Post by Yellow Pasque on 2013-03-20
> Dual-Channel memory PCs have been around since 2008. What gives?
I think you're getting confused about how dual channel works. It's not OS-specific, and your computer could tell you when it POST's (before it loads any OS) whether dual channel was in operation (my Biostar mobo tells me, but I have to turn off the splash screen to see it). Unless your BIOS/mobo is literally not detecting the second stick, then you probably have dual channel operation. Since Windows reports correct amount of memory, what you have is likely a memory addressing/remapping problem with kernel and your BIOS.

---

### Post by nibal on 2013-03-20
@Temüjin:
> I think you're getting confused about how dual channel works. It's not  OS-specific, and your computer could tell you when it POST's (before it  loads any OS) whether dual channel was in operation (my Biostar mobo  tells me, but I have to turn off the 
> splash > screen to see it). Unless  your BIOS/mobo is literally not detecting the second stick, then you  probably have dual channel operation. Since Windows reports correct  amount of memory, what you have is likely a memory addressing/remapping  
> problem with kernel and your BIOS.

That's not quite the case. Both Win 7 and Linux are in complete agreement. Windows just goes 1 step beyond in reporting that the missing memory is reserved for hardware. The problem is that 2 days ago I had only 4 GB of memory and total available memory was only 2 GB (+2 GB reserved for hardware). Since then, I installed another 4 GB of memory. How on earth, without changing any of my hardware, other than installing the extra 4 GB memory, hardware needs (reservation) jumped from 2 GB to 4 GB? I can understand that the kernel's graphic's driver reserves 1 GB equivalent to my card's VRAM, but this shouldn't increase, just by adding new memory!

BIOS definitely detects all the RAM, since userspace programs like CPU-Z in Windows or lshw in Linux report the correct total amount (8 GB). I am aware of how Dual-Channel works, and i am also aware that the kernel could very well choose to use only part of the memory available to it, due to a number of reasons.

> 1. Make sure your BIOS is up-to-date

Not quite. I will do that ASAP.

>2. Look in BIOS for IOMMU or memory remapping options

I will have to reboot for that.

>3. Test with latest kernel (an Ubuntu 13.04 64-bit LiveUSB would be handy)

No need to. I am using Ubuntu 12.04 and it agrees completely with my Windows 7. No reason for 13.04 to be any different. After all it is my problem, most people here do not know about it.:(
Besides after all the effort put in customizing for 12.04, I would hate to throw it away.

>4. Check dmesg for details. I find this command helpful:

```

~-> dmesg | grep e820
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000c776ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c7770000-0x00000000c777ffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000c7780000-0x00000000c77cffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000c77d0000-0x00000000c77dffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c77eb400-0x00000000c7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000137ffffff] usable
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x138000 max_arch_pfn = 0x400000000
[    0.000000] e820: update [mem 0xc8000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xc7770 max_arch_pfn = 0x400000000
[    0.000000] e820: [mem 0xc8000000-0xfedfffff] available for PCI devices
[    0.300406] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.300408] e820: reserve RAM buffer [mem 0xc7770000-0xc7ffffff]

```

This is indeed a very useful log. I see some worrying usable-> reserved transitions, but they are rather small (64 KB) and I could find no justification for this change in dmseg. However, you do seem to have more experience than me with this BIOS, and memory remapping seems to take place. So what do you think?
I am attaching also the whole dmesg in case you need it. I will answer about my BIOS in the next post.

TIA,
Nikos

---

### Post by nibal on 2013-03-20
>  1. Make sure your BIOS is up-to-date

Still trying. I purchased my PC 3 yrs ago BIOS v 1.90 dated 6/11/2009. Latest BIOS in ASRock is 2.30 from 1/9/2010. Unfortunately they look like they are going out of business ('cause of memory issues?). US download links do not work at all. Other links (Europe, Asia, China) they only download corrupted files ~4 KB long (~1 MB should be the upgrade). Contacting support also doesn't work. I hope it is a momentary glitch. I will try again tomorrow.

> 2. Look in BIOS for IOMMU or memory remapping options

There is nothing like that in my BIOS. The only entries for DRAM are Voltage, Timing (a whole page set to auto) and another irrelevant thing that I forget.
In the menu, my BIOS has already identified the correct memory as dual-channel with the correct size in each slot.

BR,
Nikos

---

### Post by nibal on 2013-03-21
> **nibal said:**
> >  1. Make sure your BIOS is up-to-date

Still trying. I purchased my PC 3 yrs ago BIOS v 1.90 dated 6/11/2009. Latest BIOS in ASRock is 2.30 from 1/9/2010. Unfortunately they look like they are going out of business ('cause of memory issues?). US download links do not work at all. Other links (Europe, Asia, China) they only download corrupted files ~4 KB long (~1 MB should be the upgrade). Contacting support also doesn't work. I hope it is a momentary glitch. I will try again tomorrow.

> 2. Look in BIOS for IOMMU or memory remapping options

There is nothing like that in my BIOS. The only entries for DRAM are Voltage, Timing (a whole page set to auto) and another irrelevant thing that I forget.
In the menu, my BIOS has already identified the correct memory as dual-channel with the correct size in each slot.

BR,
Nikos

 Today I was able to get in touch with AsRock's support. They replied to me immediately, and blamed the bad content to network problems, which they started checking. They also emailed me the correct BIOS images.
I now have the latest BIOS version installed, but no joy. I still get 4 GB of my memory reserved for hardware.:( At this point, since it affects similarly 2 completely different OSs (Win 7 + Ubuntu) it seems to be BIOS related, but not in an obvious way. Probably some internal memory remapping, as Temüjin suggested.

 I will pursue this further in the web and AsRock support, and (hopefully) get a solution to write about! :guitar:

BR,
Nikos

---

### Post by nibal on 2013-04-04
I got in touch with ASRock support. Installed their latest BIOS to no effect. They even sent me an updated BIOS, not in their web site. Problem persisted.
During all this time my BIOS would correctly recognize all my memory (4x2 GB) as dual synced with 1 SIMM in each slot.
ASRock's suggestion was that I should reinstall my CPU. Indeed, an Internet search revealed that Intel's i5 (and i7) are handling the dual-syncing and are very finicky
with installation. Even bent pins can cause half of the memory to disappear :-(.

First attempt to reinstall my CPU, had no effect. I am in contact with my dealer, who did the (miss)installation 3 yrs ago, and also 3 days ago. Will try again and update this thread. ;-)

Nikos

---

### Post by nibal on 2013-05-10
> **nibal said:**
> I got in touch with ASRock support. Installed their latest BIOS to no effect. They even sent me an updated BIOS, not in their web site. Problem persisted.
During all this time my BIOS would correctly recognize all my memory (4x2 GB) as dual synced with 1 SIMM in each slot.
ASRock's suggestion was that I should reinstall my CPU. Indeed, an Internet search revealed that Intel's i5 (and i7) are handling the dual-syncing and are very finicky
with installation. Even bent pins can cause half of the memory to disappear :-(.

First attempt to reinstall my CPU, had no effect. I am in contact with my dealer, who did the (miss)installation 3 yrs ago, and also 3 days ago. Will try again and update this thread. ;-)

Nikos

I checked my PC with my dealer. It turns out that there is a double hardware problem. CPU is fine, as tested with other boards. 2x2 GB DRAM is incompatible, when first installed by my dealer, 3 yrs ago. Also the blue channel in my board is toast. Cannot read anything. To top that, I have a 1156 socket CPU, and I cannot find a board for that anywhere in Greece. :(

---

