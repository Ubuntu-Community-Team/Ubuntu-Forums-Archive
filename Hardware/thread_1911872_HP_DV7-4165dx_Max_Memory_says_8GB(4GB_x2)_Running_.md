---
title: "HP DV7-4165dx Max Memory says 8GB(4GB x2) Running Ubuntu 11 64bit can I install 16GB?"
date: 2012-01-19
forum: Hardware
---

### Post by Colonel_Ingus on 2012-01-19
Computer came with Win7.
Runs Ubuntu 11.10 64bit with EXT4 now with 4GB(2GB x2).

My compatible RAM based on the manufacturer is at: [http://www.crucial.com/store/listparts.aspx?model=Pavilion%20dv7-4165dx&Cat=RAM](http://www.crucial.com/store/listparts.aspx?model=Pavilion%20dv7-4165dx&Cat=RAM)
8GB Kit (4GBx2)              
DDR3 PC3-10600 • CL=9 • Unbuffered • NON-ECC • DDR3-1333 • 1.35V • 512Meg x 64 •   •                Part #: CT2334088
OR
8GB Kit (4GBx2)              
DDR3 PC3-8500 • CL=7 • Unbuffered • NON-ECC • DDR3-1066 • 1.5V • 512Meg x 64 •   •                Part #: CT1594310


Can I install 16GB(8GB x2) instead? Will it read it?

Also if I can or if I can't, what is the difference between the 1.35V and 1.5V RAM above?

I use VirtualBox to run some apps that are only available for Windows, and on a second monitor. I need as much RAM as possible.

---

### Post by MoreOrLess on 2012-01-19
HP's site says 8GB max...
1.35V will get you slightly better battery life by relaxing the RAM latency (probably won't affect performance and that's the kit I'd recommend).

---

### Post by Colonel_Ingus on 2012-01-19
> **MoreOrLess said:**
> HP's site says 8GB max...
1.35V will get you slightly better battery life by relaxing the RAM latency (probably won't affect performance and that's the kit I'd recommend).

I read somewhere that once you go 64bit, limits don't matter...

---

### Post by MoreOrLess on 2012-01-20
> **Colonel_Ingus said:**
> I read somewhere that once you go 64bit, limits don't matter...
To the OS, maybe (there's still a limit, it's just astronomically high relative to the amount of RAM we use today).

AMD's "Champlain" CPU core still appears to have an 8GB limit though.

---

### Post by Colonel_Ingus on 2012-01-20
> **MoreOrLess said:**
> To the OS, maybe (there's still a limit, it's just astronomically high relative to the amount of RAM we use today).

AMD's "Champlain" CPU core still appears to have an 8GB limit though.

Damn

So the old: I can stick two 8GB sticks in it, but it will only read 8GB total thing.

---

### Post by Grenage on 2012-01-20
> **Colonel_Ingus said:**
> Damn

So the old: I can stick two 8GB sticks in it, but it will only read 8GB total thing.

Or it won't boot, hard to say!

---

### Post by xyzzyman on 2012-01-20
Each slot is maxed at 4GB's, so it own't even post. You definitely want matching pairs anyways as with multi-core CPU's you want your memory running into dual-channel mode. 

What apps are you running in VirtualBox? Maybe the 8GB isn't as tight as you think.

---

### Post by Colonel_Ingus on 2012-01-22
> **xyzzyman said:**
> Each slot is maxed at 4GB's, so it own't even post. You definitely want matching pairs anyways as with multi-core CPU's you want your memory running into dual-channel mode. 

What apps are you running in VirtualBox? Maybe the 8GB isn't as tight as you think.

Artisteer and Axure.

---

### Post by Colonel_Ingus on 2012-01-22
I couldn't get them to run under wine.

---

