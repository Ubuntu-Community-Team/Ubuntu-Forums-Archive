---
title: "Memory recognition"
date: 2014-10-20
forum: Hardware
---

### Post by asearle on 2014-10-20
Hi Everyone,

I have a Samsung Series 5 ultra-book running Lubuntu 14.04.

The unit comes with 4Gb RAM onboard and I have added an extra 4Gb.  Both RAM modules are recognised in BIOS.

But when I open up Lubuntu's "Task Manager" and the "System Profiler" I see only 3.4 Gb of Memory.

Can anyone explain this to me?  Is the additional module maybe not recognised?  Maybe there is a test I can run from the command line to tell me more?

Many thanks,
Alan Searle
Cologne, Germany

---

### Post by TheFu on 2014-10-20
Try running:
**more /proc/meminfo** Something like this:
```
MemTotal:        8167200 kB
MemFree:         2816036 kB
Buffers:          132600 kB
Cached:          4139768 kB
SwapCached:       320632 kB
Active:          1650788 kB

```

---

### Post by asearle on 2014-10-23
Many thanks.

I ran the command, get this result.

It's very curious that neither the 4Gb nor the 8Gb is displayed.

Any ideas why the diagnostics get this number (3.4Gb)?

Regards and thanks,
Alan

PS: I have recently installed a solid state SSD drive.  Could that play a role?

```

MemTotal:        3424888 kB
MemFree:         1966976 kB
Buffers:           52568 kB
Cached:           842588 kB
SwapCached:            0 kB
Active:           753076 kB
Inactive:         477004 kB
Active(anon):     335804 kB
Inactive(anon):     4072 kB
Active(file):     417272 kB
Inactive(file):   472932 kB
Unevictable:          32 kB
Mlocked:              32 kB
SwapTotal:       3629052 kB
SwapFree:        3629052 kB
Dirty:               260 kB
Writeback:             0 kB
AnonPages:        334972 kB
Mapped:           173292 kB
Shmem:              4948 kB
Slab:              78700 kB
SReclaimable:      57992 kB
SUnreclaim:        20708 kB

```

---

### Post by TheFu on 2014-10-23
Thanks for trying the code tags ... [], not <>. ;)  BTW - the Adv Edit makes that easier.

I can only guess that for some reason PAE or x64 isn't working on your system.  Which CPU does it have? more /proc/cpuinfo
I did find warnings about Lubuntu not using real PAE settings under some conditions. Didn't do much reading there .... you might find more.

The 3.4G usually means
* 32-bit OS (not 64-bit [x64 or amd64])
* GPU uses shared RAM, not dedicated VRAM on the GPU
* PAE extensions aren't working/enabled.  PAE allows 32-bit OSes to see much more RAM ... you can look up the max w/google.
* Memory config isn't supported - wrong type of RAM or incompatible RAM.  If you added RAM, this can be an issue vs replacing all the RAM from the same purchase. It is much less likely today than 5 yrs ago.

I doubt the SSD has anything to do with it - but I don't use SSDs. Don't trust the technology yet.  Maybe after 5 yrs more of use?

---

### Post by tgalati4 on 2014-10-24
```
uname -a
```

It should look something like:

> tgalati4@Mint14-Extensa ~ $ uname -a
Linux Mint14-Extensa 3.5.0-51-generic #76-Ubuntu SMP Thu May 15 21:19:10 UTC 2014 **x86_64 x86_64 x86_64** GNU/Linux

---

### Post by Yellow Pasque on 2014-10-24
Even if running 64-bit OS, BIOS needs to correctly support memory address remapping/"hoisting" so that some of your RAM is not used for hardware addressing.
Since this is a latpop, it is probably reserving some of the RAM for integrated graphics as well.

Bottom line? Unless you routinely use more than 3GB of RAM, don't drive yourself crazy trying to troubleshoot this.

---

### Post by asearle on 2014-10-31
I think the memory-module is shot:  I swapped the module with an identical unit and then everything was ok in the original but the other unit showed the problem (i.e. reduced memory).

But it''s strange because BIOS showed the full memory.

I'll throw out the unit.

It was fortunate that I could test on another unit because the problem hat me stumped.

Thanks for your suggestions.

Yours,
Alan

---

