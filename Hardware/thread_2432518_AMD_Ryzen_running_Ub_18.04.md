---
title: "AMD Ryzen running Ub 18.04?"
date: 2019-12-03
forum: Hardware
---

### Post by ra7411 on 2019-12-03
I'm thinking about building a machine with an AMD Ryzen cpu that also functions as a gpu.

I'm wondering if this setup will be a problem for Ub 18.04.

cpu/gpu  AMD Ryzen 5 2400G Processor with Radeon RX Vega 11 Graphics YD2400C5FBBOX


mobo      GIGABYTE B450M DS3H (AMD Ryzen AM4/M.2/HMDI/DVI/USB 3.1/DDR4/Micro ATX/Motherboard)

16 gigs ram.

Any info or opinions?

Thanks

---

### Post by mörgæs on 2019-12-03
These months we are seeing lots of posts from people having trouble with 18.04 and in general I don't recommend it, especially not for new hardware.

I can't promise that 19.10 will be free from problems but it's the best candidate.

---

### Post by CatKiller on 2019-12-04
Support for those wasn't ready in 18.04. Starting from a base of 18.04 and using the HWE kernel (or even newer), and a much newer Mesa stack from one of the PPAs that provide that, could work, but it's *much* easier to go with a newer version of Ubuntu to start with.

The 3000 APUs had a much smoother ride than the 2000 APUs but still require the newest kernel/Mesa versions.

---

### Post by ra7411 on 2019-12-04
I'm getting the idea that I might be taking on some problems/aggravation with AMD Ryzen running Ub 18.04 and maybe even later versions.
Currently, I'm running 2 AMD machines (4 yrs, 6 yrs old) w/ Ub 18.04 with few problems - maybe I should leave well enough alone.

---

### Post by CatKiller on 2019-12-04
Ryzen itself is great. The APUs (the integrated graphics part) didn't have the software in place before their release, which is why you'd want the newer stack. There was also an issue with the hardware random number generator for the recent generation of processors (it always returned -1 as its totally random number) which has been worked around, and didn't affect the 2000s that you're interested in.

Ryzen with a dedicated GPU is generally fine; Ryzen with an integrated GPU needs the newer stack.

---

### Post by mörgæs on 2019-12-04
If your computers are 4 and 6 years old I don't think there is much need for hardware upgrades. If faster processing is a priority you could try a lighter Buntu than Ubuntu.

---

### Post by ra7411 on 2019-12-04
>[COLOR=#000000]If your computers are 4 and 6 years old I don't think there is much need for hardware upgrades. If faster processing is a priority you could try a lighter Buntu than Ubuntu.<

I was mostly looking for an excuse for a fun project. [/COLOR]

---

### Post by daniel-pbt on 2019-12-27
I just received a new laptop with AMD Ryzen. I have installed Ubuntu 18:04 and it works without problems

---

### Post by muscl3s on 2019-12-28
> **daniel-pbt said:**
> I just received a new laptop with AMD Ryzen. I have installed Ubuntu 18:04 and it works without problems

Which Ryzen laptop did you purchase?  I'm considering this one and was hoping it would work without issues.
[https://www.dell.com/en-us/shop/dell-laptops/inspiron-15-5000-laptop/spd/inspiron-15-5585-laptop/nnbuc5am102sAFF?prg=1&VEN1=12578053-4485850-076b8f2a299611ea977ed2e5958396b20INT&AID=4485850&cjevent=07eee861299611ea811700ba0a240610&dgc=CJ&DGSeg=DHS&cid=198375&lid=45846&acd=12309198375458460&VEN3=810805246442050758](https://www.dell.com/en-us/shop/dell-laptops/inspiron-15-5000-laptop/spd/inspiron-15-5585-laptop/nnbuc5am102sAFF?prg=1&VEN1=12578053-4485850-076b8f2a299611ea977ed2e5958396b20INT&AID=4485850&cjevent=07eee861299611ea811700ba0a240610&dgc=CJ&DGSeg=DHS&cid=198375&lid=45846&acd=12309198375458460&VEN3=810805246442050758)

---

### Post by him610 on 2019-12-28
> looking for an excuse for a fun project
Let us know what kind of budget you have? You will get all sorts of suggestions for the fun project.

---

### Post by kurt18947 on 2019-12-28
We have two Ryzen desktops running. The first is Ryzen3 2200G on an Asrock AB350M motherboard. Those motherboards had ‘issues’ with earlier BIOS versions. Mine was a return and whoever installed a recent BIOS update so it would boot. 18.04  would not work with integral video. I installed a couple generations old AMD video card and that worked nicely. I used it like that for a few months. I recently came by a 2[SUP]nd[/SUP] monitor and wanted to use the APU’s video. I installed the 18.04 hardware enablement and still had a couple frozen video occurrences. There were some software updates installed  and am now able to use the APUs  video on two monitors with no issues.   

 
 
 The second system is recent. Wife’s desktop power supply died and took the motherboard along for the ride. Gigabyte B450 M.B.  with Ryzen 5 2600 CPU.  I put an old Nvidia video card in it, GT218 or something. That build was pretty trouble free. The only thing that doesn’t work with 18.04 is tapping the space bar to resume from suspend. That function does work with 19.10 live USB. I’m debating whether to do the HWE on her machine. Trouble free is a top priority in her case so I’m sorta reluctant to deviate from the well proven. These machines are used only for web browsing and light office type tasks. Sound, USB  and and other hardware functions as expected. Neither of us are gamers or run demanding software so we don't stress our machines. She has 6 cores/12 threads, only 2-3 of which are doing anything usually but it was the cheapest new setup I could find.

 
 
 Executive summary:  Ryzen works pretty well with Ubuntu but firmware/hardware support newer than stock 18.04 is advisable.

---

### Post by CatKiller on 2019-12-28
> **kurt18947 said:**
> I’m debating whether to do the HWE on her machine. Trouble free is a top priority in her case so I’m sorta reluctant to deviate from the well proven. 

Being on the HWE stack is the default from the 18.04.2 point release onwards, so it's a standard case. The non-HWE kernel doesn't get automatically removed, so it's just a reboot using the old kernel and removing the package of you want to stop using HWE for whatever reason.

---

### Post by kurt18947 on 2019-12-28
> **CatKiller said:**
> Being on the HWE stack is the default from the 18.04.2 point release onwards, so it's a standard case. The non-HWE kernel doesn't get automatically removed, so it's just a reboot using the old kernel and removing the package of you want to stop using HWE for whatever reason.
I'm pretty sure she's on 18.04.2 if not 18.04.3. I did see something somewhere (how's that for specifics?:p) about making a change in grub. If I find it again I might try it, if not pushing a button to bring it out of suspend isn't exactly a strain.

edit: I did run a command that installs the linux-generic-hwe-18.04 and xserver -xorg-hwe-18.04 on my machine. Perhaps the xserver portion is the magic. All I know is that it is working reliably.

---

### Post by CatKiller on 2019-12-28
> **kurt18947 said:**
> I'm pretty sure she's on 18.04.2 if not 18.04.3. I did see something somewhere (how's that for specifics?:p) about making a change in grub. If I find it again I might try it, if not pushing a button to bring it out of suspend isn't exactly a strain.

edit: I did run a command that installs the linux-generic-hwe-18.04 and xserver -xorg-hwe-18.04 on my machine. Perhaps the xserver portion is the magic. All I know is that it is working reliably.

The difference is that if you install the 18.04.2 point release (or later) you *do* get put on the HWE stack, but if you install the initial 18.04 and then upgrade to 18.04.2 (or later) you *don't* get put on the HWE stack. My point was that a lot of people, even if they're just sticking with the defaults, are successfully using the HWE stack, and that it's easy to reverse if you needed to. With it working in 19.10, even if it's a different piece of software that got fixed than what's in the HWE stack, it should work in 20.04 too.

---

### Post by daniel-pbt on 2019-12-29
[CITA = daniel-pbt; 13920333] Acabo de recibir una nueva computadora portátil con AMD Ryzen. He instalado Ubuntu 18:04 y funciona sin problemas [/ QUOTE]
[https://www.amazon.es/D509DA-BR128-Port%C3%A1til-Sistema-Operativo-Pizarra/dp/B07Z6NQ14N/ref=mp_s_a_1_1?keywords=asus+vivobook+d509da&qid=1577613855&sprefix=asus+VivoBook+d5&sr=8-1](https://www.amazon.es/D509DA-BR128-Port%C3%A1til-Sistema-Operativo-Pizarra/dp/B07Z6NQ14N/ref=mp_s_a_1_1?keywords=asus+vivobook+d509da&qid=1577613855&sprefix=asus+VivoBook+d5&sr=8-1)

---

### Post by kurt18947 on 2019-12-29
> **CatKiller said:**
> The difference is that if you install the 18.04.2 point release (or later) you *do* get put on the HWE stack, but if you install the initial 18.04 and then upgrade to 18.04.2 (or later) you *don't* get put on the HWE stack. My point was that a lot of people, even if they're just sticking with the defaults, are successfully using the HWE stack, and that it's easy to reverse if you needed to. With it working in 19.10, even if it's a different piece of software that got fixed than what's in the HWE stack, it should work in 20.04 too.

Ah, both installs started as 18.04.0 so that explains it, thanks. We'll upgrade to 20.04 once it's been out for a little while, she can tough it out for 4 months or so.

---

