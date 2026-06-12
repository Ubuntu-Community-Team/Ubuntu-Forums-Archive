---
title: "ASUS M4A78T-E locking up"
date: 2009-08-09
forum: Hardware
---

### Post by second.exodous on 2009-08-09
I was wondering if anyone owns a the ASUS M4A78T-E, or just as well if you know where I can find a log file that will tell me what happened as it locked up.

I'm installed Linux 4 time, I don't use windows, but every distro I've tried locks up.  The AMD64 version of Ubuntu ran for the longest, over a day, before locking up.  Nothing seems to be overheating, I checked right after it froze up this last time and nothing was hot, the CPU fan wasn't even on high when it happened.

Is there a log file that I can look at or something?  Now my system won't boot up, but I can use the live cd to look at files, so if anyone knows if there is a file I can look at that would be great.

Thanx,
Stan

UPDATE:  I"m putting this in if anyone happens to have the same problem.  It was the memory voltage/timings, I had to go into the bios and do quite a bit of tweaking.  You really to find a thread on your memory manufactures forums that details how to do this, it's stuff that you can't even find in the manual of the motherboard.

You need to do this:
```
Ai Overclock Tuner: Manual
Dram Timing/Driving Config
```
And set up the timings there.  I can't reboot my computer right now but with that description you should be able to find where to set things up.  It's the same bios screen where you set voltages.

Anyway, find the timings for your memory and put them in.

---

### Post by HighlyDubious on 2009-10-19
> **second.exodous said:**
> I was wondering if anyone owns a the ASUS M4A78T-E, or just as well if you know where I can find a log file that will tell me what happened as it locked up.

I'm installed Linux 4 time, I don't use windows, but every distro I've tried locks up. The AMD64 version of Ubuntu ran for the longest, over a day, before locking up. Nothing seems to be overheating, I checked right after it froze up this last time and nothing was hot, the CPU fan wasn't even on high when it happened.

Is there a log file that I can look at or something? Now my system won't boot up, but I can use the live cd to look at files, so if anyone knows if there is a file I can look at that would be great.

Thanx,
Stan

UPDATE: I"m putting this in if anyone happens to have the same problem. It was the memory voltage, I had to go into the bios and change the voltages. You go to your memory manufactures homepage and get the specs and then enter them into your bios.

Yes, I am also having problems with my M4A78T-E. Thanks to your post, I went back and adjusted the voltages on my memory, but it didn't make any difference. So I'm wondering if you have been able to keep your Ubuntu 9.04 (x64) up and running? I've had nothing but problems with Ubuntu 9.04 (x64). I've even tried the 9.10 Beta, and had the same problems.

[FONT=Tahoma][SIZE=2]My specs are:
[/SIZE][/FONT]  
[LIST]
[*][FONT=Tahoma][SIZE=2]Mobo: ASUS M4A78T-E [/SIZE][/FONT][FONT=Tahoma][SIZE=2] (BIOS v2105)[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]CPU:    AMD Phenom II X4 965 3.4Ghz[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]GPU:    ATI 4650 (OEM Generic)[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]     RAM:  8GB (4x2GB) Corsair CMX4GX3M2A1600C9 (DDR3 1600 CAS 9)[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]HD:       500GB Maxtor (SATA)[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]CD: TSST Corp CD/DVD RW SH-S204N (SATA)
[/SIZE][/FONT]
[*][FONT=Tahoma][SIZE=2]     PSU:    750 Watts (Generic)[/SIZE][/FONT]
[/LIST]
If you wouldn't mind, I'd be happy to know how your system is currently doing, and which BIOS and version of Ubuntu you are having success with (and x32? or x64?)

Any help or thoughts would be greatly appreciated.

---

### Post by second.exodous on 2009-12-07
I did a simple Google search to find exactly how to configure my memory:

```
M4A78T-E 996601
```

M4A78T-E because that's my Asus motherboard and 996601 because that's my part number of my Mushkin memory.  One of the first results gave me detailed instructions how to set up my memory, it was quite a bit of tweaking, not just the voltage, stuff that wasn't even in the manual.  So if you're just tweaking the voltage I think you need to do more.  Timings had to be changed and such.

From now on I'm subscribing to my posts so I know when someone needs more help, sorry about not replying sooner.

---

