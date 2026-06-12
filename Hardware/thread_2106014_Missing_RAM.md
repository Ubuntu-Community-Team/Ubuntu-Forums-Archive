---
title: "Missing RAM?"
date: 2013-01-17
forum: Hardware
---

### Post by ammofreak on 2013-01-17
Hi ):P:

Been trying to figure out a RAM memory puzzle. I am running Ubuntu 12.04 (64bit) with a dedicated graphics card (Nvidia) & 4GB of RAM. However, when I look at system info, only 2.9 GB of RAM is showing. This amount is verified when I run System Monitor, free, or htop. The 4 RAM sticks are seated properly as I checked my BIOS which shows the actual 4GB RAM.

My question: where is the missing 1GB of RAM?:confused:

---

### Post by dabl on 2013-01-17
Does all 4 GB show in BIOS?  What does lshw show?

---

### Post by ammofreak on 2013-01-17
Hi dabl ):P:
Thanks for the reply!

As to your inquiries: 1) Yes, 4GB of RAM showing in BIOS
                      2) lshw shows banks 0-3 of DDR RAM

---

### Post by oldfred on 2013-01-17
Then are you sure you are running 64 bit?

       32 or 64 bit
```
uname -a
```
i386 or i686 = 32-bit
x86_64 = 64-bit
```
lscpu
```

---

### Post by ammofreak on 2013-01-17
Hi oldfred ):P:
Thanks for the reply!:p

*uname -a* shows Linux (my host name) 3.5.0-21-generic..x86_64 GNU/Linux

---

### Post by dannyboy79 on 2013-01-17
what does this return?
```
cat /proc/meminfo
```

---

### Post by ammofreak on 2013-01-17
Hi dannyboy79 ):P:
Thanks for the reply!:p

Here is the O/P of *cat /proc/meminfo*

```
XXXXXXXXXXXXX ~ $ cat /proc/meminfo
MemTotal:        3081400 kB
MemFree:          319540 kB
Buffers:          253448 kB
Cached:          1306564 kB
SwapCached:         4716 kB
Active:          1521772 kB
Inactive:         964456 kB
Active(anon):     579940 kB
Inactive(anon):   353956 kB
Active(file):     941832 kB
Inactive(file):   610500 kB
Unevictable:       19348 kB
Mlocked:           19348 kB
SwapTotal:       1997820 kB
SwapFree:        1922100 kB
Dirty:               484 kB
Writeback:             0 kB
AnonPages:        941640 kB
Mapped:           209584 kB
Shmem:              4276 kB
Slab:             157788 kB
SReclaimable:     131004 kB
SUnreclaim:        26784 kB
KernelStack:        3408 kB
PageTables:        28912 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3538520 kB
Committed_AS:    3785024 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      315884 kB
VmallocChunk:   34359388668 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      162352 kB
DirectMap2M:     2981888 kB
```

---

### Post by BicyclerBoy on 2013-01-17
Part of the GPU videoram has to be mapped into 32bit memory space if BIOS does not support 64bit BAR

Chapter 9 of any nVidia driver readme..
> 64-Bit BARs (Base Address Registers)

    Starting with native PCI Express GPUs, NVIDIA's GPUs will advertise a
    64-bit BAR capability (a Base Address Register stores the location of a
    PCI I/O region, such as registers or a frame buffer). This means that the
    GPU's PCI I/O regions (registers and frame buffer) can be placed above the
    32-bit address space (the first 4 gigabytes of memory).

    The decision of where the BAR is placed is made by the system BIOS at boot
    time. If the BIOS supports 64-bit BARs, then the NVIDIA PCI I/O regions
    may be placed above the 32-bit address space. If the BIOS does not support
    this feature, then our PCI I/O regions will be placed within the 32-bit
    address space as they have always been.

    Unfortunately, some Linux kernels (such as 2.6.11.x) do not understand or
    support 64-bit BARs. If the BIOS does place any NVIDIA PCI I/O regions
    above the 32-bit address space, such kernels will reject the BAR and the
    NVIDIA driver will not work.

    The only known workaround is to upgrade to a newer kernel.


Not sure how to check the BIOS support...

---

### Post by dannyboy79 on 2013-01-17
> **ammofreak said:**
> Hi dannyboy79 ):P:
Thanks for the reply!:p

Here is the O/P of *cat /proc/meminfo*

```
XXXXXXXXXXXXX ~ $ cat /proc/meminfo
MemTotal:        3081400 kB
MemFree:          319540 kB
Buffers:          253448 kB
Cached:          1306564 kB
SwapCached:         4716 kB
Active:          1521772 kB
Inactive:         964456 kB
Active(anon):     579940 kB
Inactive(anon):   353956 kB
Active(file):     941832 kB
Inactive(file):   610500 kB
Unevictable:       19348 kB
Mlocked:           19348 kB
SwapTotal:       1997820 kB
SwapFree:        1922100 kB
Dirty:               484 kB
Writeback:             0 kB
AnonPages:        941640 kB
Mapped:           209584 kB
Shmem:              4276 kB
Slab:             157788 kB
SReclaimable:     131004 kB
SUnreclaim:        26784 kB
KernelStack:        3408 kB
PageTables:        28912 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3538520 kB
Committed_AS:    3785024 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      315884 kB
VmallocChunk:   34359388668 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      162352 kB
DirectMap2M:     2981888 kB
```yeah, it only shows 3GB, i have no clue man, sorry. maybe 1 of the slots or sticks is bad. try various combinations of 3 sticks to try to find out which stick or slot is bad possibly.

---

### Post by tlhIngan on 2013-01-17
What's your motherboard, man?

---

### Post by ammofreak on 2013-01-17
Hi everyone ):P:
Thanks again for replies!:p

Just to go over some of the pertinent info I garnered so far:

1) the BIOS is registering all 4 GB of RAM. I therefore have to assume the sticks are OK.
2) I really do not know what the m/b is other than the computer is a Dimension 8400 with a Pentium 4 CPU (3.2GHz) H/T capable for dual core.
3) Even though I am running a 64 bit OS, the m/o is only capable of 4GB with 1 GB DDR2 maximum size sticks & 4 memory slots 0-3
4) Interesting fact: ran memtest (on grub menu) at bootup & RAM is only showing 3GB! **Note**: this test would void any Nvidia addressing problems as posted, right?


Here is the memory info from *sudo lshw*:

```
*-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 1G-UDIMM
             vendor: Kingston
             physical id: 0
             serial: 2C0D2203
             slot: CHANNEL A DIMM 0
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 1G-UDIMM
             vendor: Kingston
             physical id: 1
             serial: 2C0D2303
             slot: CHANNEL B DIMM 0
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 1G-UDIMM
             vendor: Kingston
             physical id: 2
             serial: 2C0DF402
             slot: CHANNEL A DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: 1G-UDIMM
             vendor: Kingston
             physical id: 3
             serial: 2C0DE837
             slot: CHANNEL B DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
```
It is quite apparent that all 4 RAM sticks are good & memory is being registered at 4GB.

---

### Post by dabl on 2013-01-18
This situation appears to be a limitation of the Dell Dimension 8400 motherboard design:

[http://support.dell.com/support/edocs/systems/dim8400/SM/parts.htm#wp1052394](http://support.dell.com/support/edocs/systems/dim8400/SM/parts.htm#wp1052394)

Specifically "Your computer supports a maximum of 4 GB of memory when you use four 1-GB DIMMs. Current operating systems, such as Microsoft® Windows® XP, can only use a maximum of 4 GB of address space; however, the amount of memory available to the operating system is less than 4 GB. Certain components within the computer require address space in the 4-GB range. Any address space reserved for these components cannot be used by computer memory."

(This was obviously written ~10 years ago ...).

However, 3GB is plenty of memory for most typical usage scenarios with a Linux system.  If your productivity requirements often need more than that, then you also seriously need a beefier CPU than the P4.

---

### Post by ammofreak on 2013-01-18
Hi dabl ):P:

Thank you for your time & reply!:D

As you stated the upper RAM limit on the Dim8400 is 4GB. What gets me is this:

I have been using Ubuntu since 9.04 & my RAM memory alway showed 4GB or there abouts. Now with 12.04, I only get 2.9GB.

And yes, you are right:* this is an old computer!*. However, it still works beautifully even when I am running Eclipse or Aptana Studio along with 2 or 3 other programs; and a desktop littered with eye candy.:guitar:

As an aside to a previous post: I removed the Nvidia drivers completely & reverted back to X.Org Nouveau driver but to no avail! Same RAM amount.

Anyway I am declaring this post **DEAD!** Thank you again dabl & everyone else for the replies and personal time spent on my post.:cool:

---

### Post by dabl on 2013-01-18
There may have been Linux kernel code to compensate for that particular motherboard family, and being of the age that it is, that code may have been dropped as of 12.04.  They seem to be dropping older code and drivers fairly regularly now -- the same thing happened for some older video drivers in 12.10.

---

### Post by ammofreak on 2013-01-18
Hi dabl ):P:

Thanks for your persistence!:lol:

I am now wondering if a BIOS upgrade would resolve the RAM puzzle.

In any case, I am having no problems with the computer. It just bugs me when I cannot explain why something is the way it is! ](*,)

**Please** do not spend any more time on this matter. I really appreciate your efforts as obviously you have spent a deal of time trying to help me. :D

Perhaps I can return the favor & help you & others some day in the future.
Thank you again & have a great day!

---

### Post by BicyclerBoy on 2013-01-18
Previously using 32bit PAE kernel ?
The default Ubuntu kernel for 32bit is PAE ??

32bit non PAE = max ram 3.2GB (same as millions of WinXP boxes with 4GB sticks)

Don't know why your 64bit system does not see 4GB ..

cat /proc/cpuinfo

If you spoll thru the output of: 
dmesg
- you can see details about BAR 64 bit etc

---

### Post by oldfred on 2013-01-19
Post #5 shows it is 64 bit.

But sometimes border line RAM shows in BIOS, but Ubuntu does not see it. But I would think it would then only show 3 sticks not all 4?

Some have just removed RAM cleaned contacts with eraser, and then alcohol to make sure there are no eraser bits and reinstalled. It may be more just reinstalling to make sure everything is seated correctly.

---

### Post by BicyclerBoy on 2013-01-19
post #5 tells us nothing about the OP previous "working" setup.
It could have been 32bit PAE..

An eraser may make the Au contacts look nice but it bet is not ESD/SMD safe.

---

### Post by ammofreak on 2013-01-22
Hi everyone ):P:

Just wanted to add some info for update:

1) last OS was Ubuntu 12.04 (32bit)
2) the *sudo lshw* command shows all 4 sticks ( I have to assume all sticks are seated properly & working)

Thanks again for all I/P. Greatly appreciated!:)

---

### Post by Yellow Pasque on 2013-01-22
> My question: where is the missing 1GB of RAM?
Probably mapped for hardware addressing and unless you need a lot of RAM, probably nothing to worry about.
```
dmesg | grep e820
```

---

### Post by dabl on 2013-01-23
> **ammofreak said:**
> 

1) last OS was Ubuntu 12.04 (32bit)


Clearly you were running a PAE kernel, which allowed you to see and use the memory above 3.2 GB.

There were many versions of the P4 CPU, and as I recall not all of them were 64-bit capable.  Moreover, I also recall that there were motherboard designs that would support a P4, even a 64-bit capable P4, but did not provide a 64-bit address bus to the installed memory modules.  Note that on such a motherboard, the 32-bit OS with a PAE kernel, using the 32-bit memory bus, can access 4 GB of memory, but a 64-bit OS cannot.  I think that's probably your situation.  More semi-relevant info here:

[http://ubuntuforums.org/showthread.php?t=869060](http://ubuntuforums.org/showthread.php?t=869060)

---

