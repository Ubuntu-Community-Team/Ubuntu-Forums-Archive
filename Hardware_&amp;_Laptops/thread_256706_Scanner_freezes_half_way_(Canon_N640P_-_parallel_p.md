---
title: "Scanner freezes half way (Canon N640P - parallel port)"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by Sarimbi on 2006-09-13
Hello everybody,

I am new to Linux and Ubuntu, a friend has just installed it. I am trying to make a scanner work (Canon N640P - on the parallel port) using Xsane as a front end. When I start a scan from Xsane it proceeds then halts halfway through the scan. At that point Xsane is frozen. Myu Ubuntu version Dapper 6.06

Can you help? Thanks a lot.

Sarimbi

---

### Post by magog45 on 2006-11-27
I have the same problem with a HP3200c(Umax1220p) except it never starts the scan, the program just freezes. Any success out there?

---

### Post by kkkk on 2006-11-28
I have the same problem with both Canon N340P and Canon FB330P. It would really aid to have this solved.

---

### Post by 3030 on 2006-11-29
This should help if you have a Canon parallel port scanner set up (the scanner shows up when you do scanimage -L) but it freezes on halfway when scanning.

Here is the solution I found at sane-devel mailing list.
1. Go to BIOS and set parallel port mode to ECC+EPP
2. In BIOS set manually memory ranges and dma mode for the parallel port
(my settings are 378-37F, 778-77D, IRQ 7)
3. Add the following line to your /etc/modprobe.d/options file. Be sure to alter numbers accordingly to your settings from step 2.

options parport_pc io=0x378 io_hi=0x778 dma=1

4. Restart your computer
5. Try the scanner

My scanner does not work in force_nibble mode but is running smoothly when the force_nibble is commented in the canon_pp.conf file.

---

### Post by Lcarcos on 2007-10-24
I have been using my CanoScan N640P succesfully together with xsane for the last year. After upgrading to Gutsy I am getting the same problem, the scan freezes half way I have to turn it off to recover the initial possition but I am unable to scan anything with xsane.
Tired of browsing for possible solutions an trying them all, I directly tried with the scanimage command line and it works!
Is there any known problem of supporting the parallel port CanoScan N640P in the latests xsane release?

---

