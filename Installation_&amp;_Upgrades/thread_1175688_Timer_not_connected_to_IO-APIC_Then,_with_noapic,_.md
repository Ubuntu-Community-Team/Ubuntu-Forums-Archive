---
title: "Timer not connected to IO-APIC? Then, with noapic, black screen after loading screen?"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by trixx on 2009-06-01
Please help! I try to boot Ubuntu, AND Kubuntu, installers, regular it says no (I'm not sure whether it's APIC or ACPI so I'll say APIC for these purposes), and to try apic=debug and then to boot with option noapic.

I boot with noapic after, and it goes to the Kubuntu load/boot screen, and it loads all the way, then it flickers away, and then a black screen.

When I try in safe graphics mode, it flickers and goes black too.

Please help! That's BOTH computers I've had in the past that have trouble with Linux, I've never had it working 100% fully :(

EDIT: also, my specs:

nVidia GeForce 9800 GT (hooked up to a power supply thing which is occupying one of my expansion bays, because the power supply in my pc isn't powerful enough to support the card along with everything else in it, apparently, and the next level up power supply they had at the time wouldn't fit this tower)
3 GB DDR2 RAM
Intel Core 2 Quad Q6600 processor
640 GB HDD

Please help!

---

### Post by MichaelSammels on 2009-06-01
I notice you are using 3GB RAM. Out of interest have you tried the x64 edition?

Anyway, I had this problem with my laptop as well, however this problem was fixed in version 9.04 for me. Try disabling the APIC/ACPI through your BIOS and see if that makes a difference.

---

### Post by trixx on 2009-06-01
> **MichaelSammels said:**
> I notice you are using 3GB RAM. Out of interest have you tried the x64 edition?

Anyway, I had this problem with my laptop as well, however this problem was fixed in version 9.04 for me. Try disabling the APIC/ACPI through your BIOS and see if that makes a difference.

I haven't tried the x64 edition, but I didn't think to... I'm not using a 64 bit processor or anything...

I did disable one of them in the bios, but it was the opposite one to what was actually the problem... like, both are real things, but one was the problem, the other was the one i tried disabling. Couldnt find the right one, and i thought I saw something about it in the error message too, so I tried. Nothing.

---

### Post by MichaelSammels on 2009-06-01
If you are not using a 64-bit processor you cannot run x64

Have you tried disabling both options in the BIOS to see if they cause the problem? It could be your motherboard.

---

### Post by trixx on 2009-06-01
> **MichaelSammels said:**
> If you are not using a 64-bit processor you cannot run x64

Have you tried disabling both options in the BIOS to see if they cause the problem? It could be your motherboard.

Can verify, x64 doesn't work either, gets just as far, same results.

I could only find disable ACPI in my bios, where would I go for APIC?

EDIT: Also, when I go noapic, it gets farther, loading all up until it's sposed to leave the load screen... leading me to believe there may be another problem... or not. Ye're the experts.

---

### Post by MichaelSammels on 2009-06-01
That I would not know. What motherboard are you using?

---

### Post by trixx on 2009-06-02
Unsure... AM5641-E5620A, if that's a model, because that's on the outside sticker with all my specs on it :P

It's not important now I guess, as it for some reason loaded this time, when I backspaced the ro quiet splash and put noapic in, instead of just selecting the noapic option from f6.

:) Posting from Kubuntu 9.04 now. Love it :P

---

