---
title: "Total memory numbers don't match (8GB)"
date: 2009-12-08
forum: Hardware
---

### Post by Lukas666 on 2009-12-08
I have an 8GB system with Ubuntu 9.10. And a puzzle.

Ok, 8GB is:
[B][SIZE=2]8 589 934 592 bytes
[/SIZE] [/B]

[B][SIZE=2]or
[/SIZE][/B]

**[SIZE=2]8 388 608 kilobytes[/SIZE]**

(Got these numbers from google). Now, cat /proc/meminfo:

[B][B][B][SIZE=2]MemTotal:        8192556 kB
MemFree:         6278812 kB
Buffers:           38832 kB
Cached:           849552 kB[/SIZE]
[/B][/B][/B]
System monitor rounds it down to 7.8 GB

These are not rounding errors, please. So between 200-400 MB is gone somewhere (and my video is 1GB nvidia).

Any ideas? BIOS is giving me the right info, i.e. full 8GB.

L.

---

### Post by u.b.u.n.t.u on 2009-12-08
The general consensus which I learned is to go with the BIOS reporting of RAM.

---

### Post by kerry_s on 2009-12-08
> **Lukas666 said:**
> I have an 8GB system with Ubuntu 9.10. And a puzzle.

Ok, 8GB is:
[B][SIZE=2]8 589 934 592 bytes
[/SIZE] [/B]

[B][SIZE=2]or
[/SIZE][/B]

**[SIZE=2]8 388 608 kilobytes[/SIZE]**

(Got these numbers from google). Now, cat /proc/meminfo:

[B][B][B][SIZE=2]MemTotal:        8192556 kB
MemFree:         6278812 kB
Buffers:           38832 kB
Cached:           849552 kB[/SIZE]
[/B][/B][/B]
System monitor rounds it down to 7.8 GB

These are not rounding errors, please. So between 200-400 MB is gone somewhere (and my video is 1GB nvidia).

Any ideas? BIOS is giving me the right info, i.e. full 8GB.

L.


your system is reserving 2% for it's use? 8-0.16=7.84

---

### Post by Lukas666 on 2009-12-08
> **kerry_s said:**
> your system is reserving 2% for it's use? 8-0.16=7.84

How do you know that? You just calculated that? Where can I read more about this?

Thanks,
L.

---

### Post by HappyFeet on 2009-12-08
The amount of your ram is correct, and have not lost any. Manufacturers and operating systems use 2 different methods of reporting ram and hard drive sizes. It has been like that since PC's began. Manufacturers consider 1000mb=1gb. The OS sees 1024mb=1gb.

I have 6gb of ram, but ubuntu sees it as 5.8

It's the same on every computer in the world.

[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
"*The industry has coped with the dual definitions because system memory (RAM) typically uses the binary meaning while disk storage uses the SI meaning, but there are exceptions like diskettes and Compact Disks. The International System of Units defines no units for digital information but the SI prefixes may be applied outside the contexts where base units or derived units would be used*."

---

### Post by HappyFeet on 2009-12-08
> **kerry_s said:**
> your system is reserving 2% for it's use? 8-0.16=7.84

Not true.

---

### Post by Lukas666 on 2009-12-08
> **HappyFeet said:**
> The amount of your ram is correct, and have not lost any. Manufacturers and operating systems use 2 different methods of reporting ram and hard drive sizes. It has been like that since PC's began. Manufacturers consider 1000mb=1gb. The OS sees 1024mb=1gb.

I have 6gb of ram, but ubuntu sees it as 5.8

It's the same on every computer in the world.

[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
"*The industry has coped with the dual definitions because system memory (RAM) typically uses the binary meaning while disk storage uses the SI meaning, but there are exceptions like diskettes and Compact Disks. The International System of Units defines no units for digital information but the SI prefixes may be applied outside the contexts where base units or derived units would be used*."

I know what you are talking about and you are wrong.

The number of kilobytes reported by BIOS and the number reported by /proc/meminfo:
are different. And they do use same units.

---

### Post by u.b.u.n.t.u on 2009-12-08
> **Lukas666 said:**
> 
The number of kilobytes reported by BIOS and the number reported by

If you find an answer I would be most interested.

RAM is sold by memory size and the BIOS reports RAM. That is the standard that I learned and I am yet to hear of a better more accepted measurement.

---

### Post by Lukas666 on 2009-12-08
> **u.b.u.n.t.u said:**
> If you find an answer I would be most interested.

RAM is sold by memory size and the BIOS reports RAM. That is the standard that I learned and I am yet to hear of a better more accepted measurement.

And I agree. But why Ubuntu does not have access to all the bytes? What's happened to them (the missing ones)? Could it be the BIOS stealing them?

L.

---

### Post by u.b.u.n.t.u on 2009-12-08
> **Lukas666 said:**
> And I agree. But why Ubuntu does not have access to all the bytes? What's happened to them (the missing ones)? Could it be the BIOS stealing them?

L.

Indeed, one of life's many riddles! ;)

---

### Post by HappyFeet on 2009-12-08
> **Lukas666 said:**
> 

The number of kilobytes reported by BIOS and the number reported by /proc/meminfo:
are different. And they do use same units.

I guess I misunderstood the nature of your question. Sorry for wasting your time, and take care.

---

### Post by Yellow Pasque on 2009-12-08
You should be grateful that your system can use that much. A lot of recent motherboards still don't have proper BIOS support for >4GB RAM

---

### Post by Mike'sHardLinux on 2009-12-08
> **Temüjin said:**
> You should be grateful that your system can use that much. A lot of recent motherboards still don't have proper BIOS support for >4GB RAM

Really? Like which ones? I plan to upgrade soon and want to avoid those. I find that very strange as my system is almost 3 years old, and I have had 8GB on it (with original BIOS) from the beginning. Are you sure those are "recent" boards?

---

### Post by Yellow Pasque on 2009-12-08
Look through the recently closed x86-64 forum and witness the number of threads about RAM usage.

---

### Post by Mike'sHardLinux on 2009-12-09
hmmmm.....yaa....found one thread about Tyan K8WE....released in 2005....and another thread about Asus P5VM, about 2 (or 3)years old......couple of threads about laptops. I doubt there are many recent boards with problems supporting >4GB....maybe a very small number.

---

### Post by Lukas666 on 2009-12-09
> **Mike'sHardLinux said:**
> Really? Like which ones? I plan to upgrade soon and want to avoid those. I find that very strange as my system is almost 3 years old, and I have had 8GB on it (with original BIOS) from the beginning. Are you sure those are "recent" boards?

I know the problem. Some MBs have problems with 4 sticks sitting in them (usually that's all slots taken). And that usually requires a significant voltage increase on one of the bridges (north?). 

Also, New MBs are more and more "memory picky", always check the manafacturer's website for all supported memory brands and models.

---

### Post by Lukas666 on 2009-12-09
> **Temüjin said:**
> Look through the recently closed x86-64 forum and witness the number of threads about RAM usage.

Thanks, I'll check it.

L.

---

