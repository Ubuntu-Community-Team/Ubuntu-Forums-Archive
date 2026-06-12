---
title: "Kubuntu on a 1GHz i586, doable?"
date: 2009-06-18
forum: Hardware
---

### Post by Nick255 on 2009-06-18
I was wondering how Kubuntu would work on a system with an i586 CPU.  Even though it runs at 1GHz, would the lack of CMOV and other i686 instructions cause any problems?

Update - it is an Xcore86 CPU

---

### Post by abn91c on 2009-06-18
> **Nick255 said:**
> I was wondering how Kubuntu would work on a system with an i586 CPU.  Even though it runs at 1GHz, would the lack of CMOV and other i686 instructions cause any problems?

Update - it is an Xcore86 CPU

have you tried the live cd? most times the only "show stopper" is the video card and not enough RAM

---

### Post by Nick255 on 2009-06-19
> **abn91c said:**
> have you tried the live cd? most times the only "show stopper" is the video card and not enough RAM

The system in question won't be available until august.  I was just wondering if there would be any problems due to the lack of i686 instructions (cmov, sse, etc)?  I am mostly concerned about Flash, though I see some people have run Flash 10 on a Via C3.

---

### Post by stinger30au on 2009-06-19
i reckon it will go so long as like poster #2 said if it has enough ram, say 384 meg or so and a half decent video card, you will be cooking with gas in no time

---

### Post by 00b00nt00 on 2009-06-20
i586? Geez. That went out with the Pentium MMX!

Seriously, try Ubuntu netbook remix. Many netbooks have an Intel Atom processor (spits on the floor). The Atom is built around the 586 instruction set, so you may be in luck.

---

### Post by Nick255 on 2009-06-20
> **00b00nt00 said:**
> i586? Geez. That went out with the Pentium MMX!

Seriously, try Ubuntu netbook remix. Many netbooks have an Intel Atom processor (spits on the floor). The Atom is built around the 586 instruction set, so you may be in luck.

Actually, the Via C3 is also a 586 and so is the Xcore86 (like the Atom, but only 1.2 watts).

---

### Post by 00b00nt00 on 2009-06-20
My understanding is that VIA's offerings, and particularly the Nano, wipe the floor with Intel's Atom. If an Atom can run Ubuntu, I think you'll have no problems (with the CPU). I'm not a systems builder, so beyond that I'm afraid I can't help out much.

---

### Post by Nick255 on 2009-06-21
> **00b00nt00 said:**
> My understanding is that VIA's offerings, and particularly the Nano, wipe the floor with Intel's Atom. If an Atom can run Ubuntu, I think you'll have no problems (with the CPU). I'm not a systems builder, so beyond that I'm afraid I can't help out much.

No, the chip is an Xcore86.  It is similar in performance to an 800MHz P3 or the AMD Geode LX800.  The AMD Geode LX is closer because it also uses the i586 instruction set and does not support sse, cmov, or other i686 instructions.  It also includes 1GB of RAM (256MB and 512MB versions also exist).

---

### Post by 00b00nt00 on 2009-06-22
I think my point was that if Ubuntu worked on other i586 chips, then the xcode flavour should work as well.

I have run Ubuntu satisfactorily on an 800Mhz PIII. Web pages loaded with Flash gave the CPU a hard time, though I could view standard definition videos in Youtube. Would I actually bother building a system with that level of performance? Well, no, but seeing as I inherited it, sure.

In reality, if you succeed in getting Ubuntu to run on that CPU, you may be uninspired by its performance.

---

### Post by Nick255 on 2009-06-29
> **00b00nt00 said:**
> I think my point was that if Ubuntu worked on other i586 chips, then the xcode flavour should work as well.

I have run Ubuntu satisfactorily on an 800Mhz PIII. Web pages loaded with Flash gave the CPU a hard time, though I could view standard definition videos in Youtube. Would I actually bother building a system with that level of performance? Well, no, but seeing as I inherited it, sure.

In reality, if you succeed in getting Ubuntu to run on that CPU, you may be uninspired by its performance.

Well, it is a netbook designed to compete with some of the ARM based ones, so I fully expect the performance of a netbook and not a mini-laptop like some of the newer so called netbooks.

---

