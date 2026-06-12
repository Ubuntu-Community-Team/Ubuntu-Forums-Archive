---
title: "Ubuntu is using to much of memory"
date: 2009-02-10
forum: Hardware
---

### Post by tigga on 2009-02-10
hello
My laptop is a Toshiba with centrino processor(not centrino duo).
any way , ubuntu(8.04) is using about 300 MB of my 512 MB without executing any program.
I tried using the xfce but nothing happened.

this is what "free" give me
```
             total       used       free     shared    buffers     cached
Mem:        506392     495596      10796          0       4972     283624
-/+ buffers/cache:     207000     299392
Swap:      1485972     131908    1354064
```

this is the "top" header
```
top - 16:02:07 up  1:30,  3 users,  load average: 0.09, 0.23, 0.45
Tasks: 137 total,   2 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.3%us,  0.3%sy,  0.0%ni, 96.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    506392k total,   492860k used,    13532k free,     5272k buffers
Swap:  1485972k total,   131900k used,  1354072k free,   278400k cached
```

Please help me and thanks in advance.

---

### Post by OrangeCrate on 2009-02-10
It's nothing to worry about, it's because of disk caching. See how it works here:

**Linux Memory Management or 'Why is there no free RAM?'**

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by lloyd_b on 2009-02-10
By the looks of it, you're actually *using* about 200MB (the 207000 number after "-/+ buffers/cache:").

I would consider this pretty high, except in one case - if that machine is using a cheap Intel video chip, then a big chunk of memory is being grabbed by the video driver, in which case that 200MB looks pretty reasonable (those Intel chips use system RAM instead of having dedicated video RAM like most graphics cards).

Lloyd B.

---

### Post by airtonix on 2009-02-10
Ram not used is ram wasted. welcome to the world of caching.

---

### Post by stchman on 2009-02-10
> **tigga said:**
> hello
My laptop is a Toshiba with centrino processor(not centrino duo).
any way , ubuntu(8.04) is using about 300 MB of my 512 MB without executing any program.
I tried using the xfce but nothing happened.

this is what "free" give me
```
             total       used       free     shared    buffers     cached
Mem:        506392     495596      10796          0       4972     283624
-/+ buffers/cache:     207000     299392
Swap:      1485972     131908    1354064
```

this is the "top" header
```
top - 16:02:07 up  1:30,  3 users,  load average: 0.09, 0.23, 0.45
Tasks: 137 total,   2 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.3%us,  0.3%sy,  0.0%ni, 96.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    506392k total,   492860k used,    13532k free,     5272k buffers
Swap:  1485972k total,   131900k used,  1354072k free,   278400k cached
```

Please help me and thanks in advance.

That sounds about right.  My 32 bit installs use in the neighborhood of 250MB RAM.  My 64 bit installs use about 500MB memory.

I think 512MB is considered the minimum RAM to have Ubuntu be comfortably usable.  RAM is really cheap so I recommend you upgrade to about 2GB.

---

