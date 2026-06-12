---
title: "Get critical error when cpu load is about 70% or more"
date: 2015-06-12
forum: Hardware
---

### Post by phs2004 on 2015-06-12
Hi, 

Dont know whats wrong whit my ubuntu server 14.04 lts. Is it motherboard, cpu or memory. Did a memtest for about 2h no erros. Not overheated. Dont realy know what to do. 
Cant buy all that new hardware only the part thats broken. Tested all harddrivers for errors all fine.

Look at the picture at the critical error. 


[COLOR=#000000][FONT=Times New Roman]Intel(R) Core(TM) i7 CPU 920 @ 2.67GHz
[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman]Gigabyte EX58-UD3R
[/FONT][/COLOR]6gig ram. 

[URL="https://www.linuxburken.com/mySpecs.html"]
[/URL]
Anyone know what cold be wrong?

---

### Post by tgalati4 on 2015-06-13
Modern CPU's have multiple cores with on-die cache that can be accessed by all of the CPU's.  It appears that you have a cache memory error because you are getting the same memory address by all 8 CPU's trying to access it.  Is the processor still under warranty?

But, to be sure, burn a USB with 15.04 and try to load that and see if you get the same error with a newer kernel.

---

### Post by Yellow Pasque on 2015-06-13
If it is bad cache, perhaps raising the CPU voltage a little will help. Obviously, make sure your cooling system can handle the extra heat.

---

### Post by phs2004 on 2015-06-13
Ok tanks going to test :) Be back whit answer. 

Edit: FFmpeg on whit V1.3125 up from V1.2525 (standard) sensors says 77[COLOR=#252525][FONT=sans-serif]°C warn at 80[/FONT][/COLOR][COLOR=#252525][FONT=sans-serif]°C. To test if it kraches then Im testing 15.04. If it works buy new cooler. [/FONT][/COLOR]

---

