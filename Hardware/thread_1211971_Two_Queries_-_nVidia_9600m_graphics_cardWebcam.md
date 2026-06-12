---
title: "Two Queries - nVidia 9600m graphics card/Webcam"
date: 2009-07-13
forum: Hardware
---

### Post by Oizu on 2009-07-13
Hi, ive just installed Ubuntu 9.04 on my Acer Aspire 8930, and have been having a few issues.

My first issue is something im not particularly sure even is an issue, and is about my grahics card, when i was trying to sort out my sound issue i stumbled across this:

> 01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GS (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0145
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at 6000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

when i typed 

> lspci -vinto the terminal.

The key thing here (i think) is that it says the memory is 256mb, what puzzles me is that its a 512mb card. (GeForce 9600m GS 512mb) So surely that should read 512mb? Am i just worrying over nothing here or is there a way to change this?

My second query is more general, this laptop came with a load of integrated feature such as a microphone + webcam, i cant see any way to use these, can I?

Thanks

---

### Post by Pratt on 2009-07-28
Did you sort out your sound problem.  If so, can you tell me how, because I have got exactly the same problem, and being completely new to linux of any variety, I am just desperately begging for help, but not getting any from any quarter.  I have been lurking on these forums for over a week now, I've written a couple of queries to people who have the same sound problem on the same type of equipment (Acer Aspire  8930g) but all to no avail!   No one has even had the decency to reply.

I'm beginning to think that the ubuntu community are just as elitist as the Microsoft communities are, not prepared to help any newbies. Ubuntu stands for humanity.  Well not much humanity shown here, I think!  Sorry, I'm not having a pop at anyone, it's just my frustration at not being able to get this laptop working properly.  Good luck in your endeavors!

---

