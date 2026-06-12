---
title: "Kernel/syslog/drivers/RAM   experts - please read"
date: 2015-09-17
forum: Hardware
---

### Post by NS on 2015-09-17
[COLOR=#000000]
[/COLOR]I would like to find out exactly how much memory is available to user, and how much memory is being used by device drivers and kernel.  I am aware of all the related command line tools like * lshw, lspci, dmidecode, dmesg *etc.  and have looked at all the info that they can provide. 

But, does anyone know which lines in syslog i should refer to, so that I can figure out exactly how much memory Ubuntu kernel is getting (including Graphics, drivers etc) from BIOS ?  Is there any document to help me understand easily the cryptic messages i see in syslog regarding memory allocations at various points ?  Looking at syslog and using a calculator to convert all the HEX numbers into decimals  will be more tedious process, but this is the only way i can think of,  to go beyond what is provided by the command line tools i mentioned above.[COLOR=#000000]
[/COLOR]
Do you know if the entries like "[COLOR=#000000]*Total Memory	: 3070948 kB*", as reported by utilities such as "hardinfo", include the device drivers or exclude the drivers ?  By reading a Intel whitepaper on their DVMT for integrated chipsets, one can see that *atleast some of the RAM* is reserved by BIOS, for video processor and will not be seen by OS.  I do not know how other device drivers work in tandem with BIOS & OS.  [/COLOR]

---

### Post by tgalati4 on 2015-09-17
That's a tough question. And I am certainly not a kernel/syslog/driver/RAM expert.  I don't know if there is a simple command that will break it down that way.  You can go through a snapshot of your memory by examining /dev/mem (but don't change it otherwise you will instantly crash your system).  You can look at /proc/meminfo to get more detailed memory allocation.

> tgalati4@Mint17 ~ $ cat /proc/meminfo
MemTotal:        2040640 kB
MemFree:          298436 kB
Buffers:           39216 kB
Cached:           694744 kB
SwapCached:       132208 kB
Active:          1014180 kB
Inactive:         597140 kB
Active(anon):     716488 kB
Inactive(anon):   301796 kB
Active(file):     297692 kB
Inactive(file):   295344 kB
Unevictable:          16 kB
Mlocked:              16 kB
SwapTotal:       2578428 kB
SwapFree:        2133048 kB
Dirty:                56 kB
Writeback:             0 kB
AnonPages:        793488 kB
Mapped:           135108 kB
Shmem:            140924 kB
Slab:              57036 kB
SReclaimable:      31180 kB
SUnreclaim:        25856 kB
KernelStack:        3832 kB
PageTables:        36660 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3598748 kB
Committed_AS:    4450228 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      541388 kB
VmallocChunk:   34359189084 kB
HardwareCorrupted:     0 kB
AnonHugePages:    174080 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       45888 kB
DirectMap2M:     2041856 kB


The command *free* shows what RAM is available to the user, but between shared RAM and cache, it is constantly changing and not really useful unless you run out of RAM are start hitting swap.

Why do you want to know the exact RAM use by the system?

Some reading:  [http://www.tldp.org/HOWTO/KernelAnalysis-HOWTO-7.html](http://www.tldp.org/HOWTO/KernelAnalysis-HOWTO-7.html)

---

### Post by NS on 2015-09-22
Thanks  tgalati4.  It was just a curiosity for me because I came across RAM issues in my old hardware running Ubuntu.  The graphics chipset on this machine (Intel 915GV) reserves  some Fixed memory, through BIOS and then borrows some more dynamically after OS initialization, from the OS system RAM.  How much exactly it will borrow from OS is unclear (even after talking to Intel support and reading their docs).  So, my intention was to skim through syslog, because going through the command line tools for this is not giving me a clear picture of  how exactly RAM is being consumed (by BIOS, drivers, OS, graphics chipset etc.).   I was hoping that the kernel guys would have  faced similar problems during their development and would have some sort of tool to easily sort through syslog.  (PS:  I am yet to go through the docs you gave me). 
 

[COLOR=#000000][/COLOR]

---

### Post by tgalati4 on 2015-09-22
If you are running the i915 module then there are a lot of switches to play with.  Unfortunately, none show video RAM in use:

```
modinfo i915
```

You would have to dig into the video module and look at the code or development documentation to see how video RAM is requested and provided by the system.

---

