---
title: "Acer Aspire 5920 help"
date: 2008-07-16
forum: Hardware
---

### Post by derrick991 on 2008-07-16
I hate Vista so I decided to install Ubuntu. I've installed feisty, gutsy, and currently have hardy.

I have two problems. 
The first problem is that on startup, i'm taken to an "initramfs" prompt, this is easy to deal with though because i simply type exit and Ubuntu continues to boot. This problem did occur in feisty and gutsy as well.
The second problem is that when i run any big program, it takes up 100% CPU and slows my system to a creeping halt. The program in particular is FlightGear which shouldn't really suck up all my proc. power. This does occur on other programs.
Any help would be very much appreciated.

My specs are:
 1.6Ghz intel core 2 duo
 3 GB ram
 and whatever the integrated graphics are.

Thanks

---

### Post by phidia on 2008-07-16
> **derrick991 said:**
>  The program in particular is FlightGear which shouldn't really suck up all my proc. power. This does occur on other programs.
Any help would be very much appreciated.

My specs are:
 1.6Ghz intel core 2 duo
 3 GB ram
 and whatever the integrated graphics are.

Thanks

Knowing the specific gpu/video card is sort of important. 
Open a terminal and paste this into it: > lspci | grep VGA
You may have the GMA 950 those cards use system ram and from what all the gamers say they are not as good as a dedicated gpu for rendering-meaning they will draw a lot from your system when video or a game requires high fps.

---

### Post by derrick991 on 2008-07-16
ok the graphics are: Intel GM965/GL960

---

### Post by derrick991 on 2008-07-17
any ideas on the initramfs thing?

---

