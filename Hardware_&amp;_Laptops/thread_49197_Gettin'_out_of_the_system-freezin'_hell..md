---
title: "Gettin' out of the system-freezin' hell."
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by fresco on 2005-07-15
This is my everyday problem:

1. Power on system.
2. Loading Ubuntu (or some other system)
3. Working for about 5 mins - system freezes. I call these freezes complete, because pointer doesn't move and nothing's happening.
4. Reset. Often it is multiple resets, because system cannot run POST succefully (without any sound events). Display doesn't turn on. I thought It might be that Power Supply Block doesn't send 'Power Good' signal but then CD-ROM wouldn't power-on, but it does. (Or I'm not right?)  
5.Steps 2-4 repeating about 2-3 times.
6. After that there aren't any problems - computer may work for days without trouble.

All this stuff repeats every day (when I turn on my PC in the morning). I have found these problems are OS-independent (system may freeze even in BIOS), ACPI - independent, HDD - independent (Running Knoppix. But if HDD would be damaged BIOS wold identify it anyway).

Where's the problem? Your ideas. :-k 

Sorry, it is not about Ubuntu, but I believe here are many good specialists who can help me with this thing.  
Every comment is appreciated! 
Thanks!

---

### Post by varunus on 2005-07-15
What are your system specs?  Processor?  Power Supply?  Hard Drives?  RAM?  etc?

---

### Post by fresco on 2005-07-15
AMD Duron 1200Mhz
Mb: Elitegroup K7VTA3 - KT333
Ram: 256 MB
Codegen 250W power supply
Video: GeForce MX400  64 MB ram
Realtek ethernet card
Creative Sound Blaster PCI 128 
SONY CD-ROM 52x
Seagate Barracuda 40Gb HDD

---

### Post by fresco on 2005-07-16
Any ideas?  O:)

---

### Post by rikai on 2005-07-16
have you tried a different PSU?
That's the first thing i'd reccomend, that's a rater low wattage PSU anyway..
if that doesnt solve the problem, test your memory in another system.

---

### Post by moopere on 2005-07-16
[QUOTE=fresco]AMD Duron 1200Mhz
Mb: Elitegroup K7VTA3 - KT333
Ram: 256 MB
Codegen 250W power supply
Video: GeForce MX400  64 MB ram
Realtek ethernet card
Creative Sound Blaster PCI 128 
SONY CD-ROM 52x
Seagate Barracuda 40Gb HDD[/QUOTE]

I don't want to offend you, and folks can be really sensitive about this sort of thing but, FWIW, I'd say your problem is right here:

"Mb: Elitegroup K7VTA3 - KT333"

I would be hard pressed to think of a lower end motherboard than this (see:cheap, nasty, unstable, etc).

Elitegroup for years have produced really bad boards.  

I'm not trying to be a snob, there are plenty of economy boards that give reasonable results (not great, but reasonable), Abit, Gigabyte etc come to mind.


In addition, I'd really like to know who makes the following from your list:

Ram: 256 MB
Video: GeForce MX400  64 MB ram
Realtek ethernet card

I'd start testing with memtest86 (from cold boot run for a day or more).  burnCPU, bonnie++ etc etc etc.  You can probably work out whats wrong, but I'd just about lay money on your motherboard being the cause.

Best regards,
Craig

---

