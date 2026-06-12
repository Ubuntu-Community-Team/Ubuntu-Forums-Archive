---
title: "CPU problem"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by Jad on 2005-05-04
Greetings
my computer keep freezing, CPU temp gives 89C with 2445RPM for CPU fan, 
and I have extra cooling fan, the computer is really cold, and cant be 89C CPU temp
i'm not sure what could be the problem, is it hardware problem or software problem, but I think its a hardware problem, because I have checked the CPU temp and CPU fan rpm from the bious system health 

if its the CPU, how to check if its broken or not, or is it a conflict or blah I don't know, I'm not into hardware.. 
please advise.. 

```
jad@ubuntu:~ $ sudo head /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 2.66GHz
stepping        : 9
cpu MHz         : 2014.123
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
```

```
Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

```

---

### Post by joekr on 2005-05-04
I'm not sure *why* your temps are high or why your computer is crashing.

**BUT** I am sure that your 2.6 Ghz chip is currently operating at an underclocked speed... 2.0 Ghz.

---

### Post by Jad on 2005-05-04
how so ?

---

### Post by joekr on 2005-05-04
Your CPU Mhz value is 2014.123 = 2.0 Ghz

It should be around 2600.  You're operating 600 Mhz (.6 Ghz) slower than you should.

This is VERY odd.  Since you are running at slower then recommended speeds, your computer should be much cooler then 'average'.  I would double check to see if your fan is indeed spinning.

Have you asked anyone to take a look at the hardware?  As unlikely as it might seem, perhaps someone recognized the fan was not working, and therefore underclocked it to compensate for the overheating.

Something is majorly wrong.  I wouldn't recommend keeping the computer on until you verify the fan is indeed working.  Once you check that out, go into your bios, and look for a menu called Jumperless settings, and adjust your settings to 'default' or something along those lines.

---

### Post by Jad on 2005-05-04
the fan is working properly, I have touched the metallic peice under the fan and its cold just like just arrived from alaska, also FAN rpm shows 2445rpm 

on the last system freez, I have unpluged the fan in about 20second to touch the cpu itself, and it was cold.

---

### Post by DutchLau on 2005-05-04
Best option: Get an AMD  :razz: 

Wow, I'm dumbfounded also. Maybe you have a problem with your thermometer? Check in your Bios to see if your CPU overclocking feature is at "auto" or something like that. 

I had this before also. It kept saying that my Pentium 3 1Ghz was at 100C, but it *was* stable. Strange 

Let us know once you've solved your problem,

DutchLau

---

### Post by Jad on 2005-05-04
my problem is, its saying its about 89, and 100 last check and its not stable

dutchlau machine like this one AMD 64 3200+ 939-pins, Asus A8V - Deluxe, 1024 PC400 DDR Ram, 256MB GeForce FX 5200 AGP 8x, 160 GB SATA HDD how much will cost me ?

---

### Post by Jad on 2005-05-04
on the other hand, why my CPU underclocked ?
cpu MHz         : 2014.200

---

### Post by phvash on 2005-05-07
Intel CPUs lower their frequencies if they approach a certain critical temperature (as opposed to some AMD ones that will just die). 

You should try the dmesg command and look for messages about clock modulation.

---

### Post by Paulus on 2005-05-07
what does your bios report for your temps?   This should accuratly determine whether your CPU is throttling due to hight temps.   Are you overclocked?   try reverting the bios to default values, it's possible your bios misdetected your cpu and is using incorrect FSB and Multiplier values.

---

### Post by D4_B34M on 2005-05-07
Have you overclocked your CPU? I mean more than the normal, clocking too much breaks the CPU and once it's broken the speed goes down and it starts to crash.

But if you haven't overclocked and this still happens (try for example some live Linux to check that isnt because of Ubuntu), if you have still warranty, take it back to the seller.

---

