---
title: "Ryzen 7, with MSI B350 motherboard"
date: 2018-03-15
forum: Hardware
---

### Post by Dedalo on 2018-03-15
I have bought a new computer with a Ryzen 7 1700 processor, and MSI B350 motherboard. It is a workstation, so people in charge of computers at my work were trying to install ubuntu 16.04. There were some issues, I've been told that the 32 bit version of ubuntu worked well, but they couldn't make it work yet with the 64 bit version of ubuntu. They were trying to install the drivers at this point. I thought I could get some support from these forums.

By the way, I would also like to know if gfortran compiller works properly on ryzen 7 architecture, and if mpi works also on these processors.

Thanks in advance.

---

### Post by QIII on 2018-03-15
Hello!

Can you give us some details about what you mean by "couldn't make it to work"?

What drivers are they attempting to install?

---

### Post by Dedalo on 2018-03-15
> **QIII said:**
> Hello!

Can you give us some details about what you mean by "couldn't make it to work"?

What drivers are they attempting to install?

Hi. I actually don't know the details, because I am not working on it, and the guy who is on it just told me when I saw him today. I gave them the drivers that came in the box of the motherboard, but I don't know if those are useful for ubuntu.

Thanks for your reply!

---

### Post by QIII on 2018-03-15
The driver disk that comes with a mobo is typically for Windows and wouldn't work for Linux if you needed it -- which you probably don't.  

If Ubuntu installed and it's running, the Linux drivers already baked into the kernel are working.

I just built a Threadripper box with a 1950X on an ASRock Taichi.  No additional drivers required, except for my graphics card.

---

### Post by Dedalo on 2018-03-16
Ok. Thanks!

---

### Post by Dedalo on 2018-03-20
Hi. I finally have the computer, and is working fine. However, there seems to be some issue with the generic graphic card in the motherboard, because they had to put another graphic card. I don't know if there is some problem of compatibility with the motherboard and the cpu.

The other issue I wanted to ask is about the performance of the ryzen cpu with this motherboard. I've downloaded hardinfo, and made the benchmarks, and all benchmarks give 1550Mhz for the cpu clock, which is far behind the 3Ghz reported in amd webpage as the base clock: [https://www.amd.com/en/products/cpu/amd-ryzen-7-1700](https://www.amd.com/en/products/cpu/amd-ryzen-7-1700) (I think this has to do with the fact that hardinfo detects 16 virtual processors, so it seems like each processor capability is divided by two, which sounds reasonable).

---

### Post by Yellow Pasque on 2018-03-20
> However, there seems to be some issue with the generic graphic card in the motherboard, because they had to put another graphic card.

Huh? The Ryzen 1700 doesn't have an integrated GPU. The video ports on the mobo are for those who use an APU.

> all benchmarks give 1550Mhz for the cpu clock, which is far behind the 3Ghz reported in amd webpage as the base clock

That's probably the idle speed. If it really is stuck at 1.5 GHz under full load, perhaps someone has been playing in the BIOS. [https://www.reddit.com/r/Amd/comments/6c0qw8/1700_gets_stuck_at_15_ghz/](https://www.reddit.com/r/Amd/comments/6c0qw8/1700_gets_stuck_at_15_ghz/)
Consider resetting the BIOS and/or updating the BIOS if it's stuck at 1.5GHz

> I think this has to do with the fact that hardinfo detects 16 virtual processors 

Yeah, it's an 8 core, 16 thread CPU, so that's expected.

> so it seems like each processor capability is divided by two, which sounds reasonable.

That doesn't make sense. Just because a CPU supports Multi/Hyper threading, that will not make it report half speed.

---

### Post by Dedalo on 2018-03-21
Ok, thanks. I'll try to update the bios, and if it that doesn't work I'll reset it. Thank you very much.

> That's probably the idle speed. If it really is stuck at 1.5 GHz under full load, perhaps someone has been playing in the BIOS. [https://www.reddit.com/r/Amd/comment...uck_at_15_ghz/]("https://www.reddit.com/r/Amd/comments/6c0qw8/1700_gets_stuck_at_15_ghz/")
Consider resetting the BIOS and/or updating the BIOS if it's stuck at 1.5GHz

How do I know if it is the idle speed? the benchmarks are some intensive tasks, like FFTs, and things like that. I don't know which speed is hardinfo actually reporting, but I would expect from a benchmark to report the full load speed.

BTW, if you have a link that explains how to update the bios in ubuntu, that would be of great help also.

---

### Post by Dedalo on 2018-03-21
I entered the BIOS, and set all to default. That worked, now the benchmarks gives 3Ghz. However, the BIOS is version E7A34AMSM00, BIOS build date: 04/10/2017, so I would like to update it if that has any advantage.

---

### Post by Yellow Pasque on 2018-03-21
> **Dedalo said:**
> if you have a link that explains how to update the bios in ubuntu, that would be of great help also.

You don't do it through Ubuntu/Linux. [https://www.msi.com/files/pdf/How_to_flash_the_BIOS.pdf](https://www.msi.com/files/pdf/How_to_flash_the_BIOS.pdf)

---

### Post by Dedalo on 2018-03-23
Thanks!

---

