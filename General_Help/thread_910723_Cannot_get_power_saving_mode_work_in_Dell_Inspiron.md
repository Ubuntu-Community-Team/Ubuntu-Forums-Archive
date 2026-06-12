---
title: "Cannot get power saving mode work in Dell Inspiron 530"
date: 2008-09-04
forum: General Help
---

### Post by vshun on 2008-09-04
Hi,

I bought Dell Inspirin 530 slim mode (it was Dos version and so put Hardy 64 bit on it myself). My problem is that I am not able to get power saving mode work on it. 
Both Suspend and Hibernate operations never recover (have to reboot computer). I googled the issue and found similar problem with some other Dell model which someone resolved by updating nVidia driver. 
Well, this computer does have embedded Intel video card (3100???) which, by the way, only gives you VGA output and not DVI. In any event, I assumed Intel is a safe option and not sure if it is causing a problem. 
Does anyone uses power saving mode successfully with Inspiron 530 and if so - what graphics card and options worked for you?

Thanks,

Vadim.

---

### Post by BrewBelly on 2008-10-28
Same prob here with Inspiron 1300.

---

### Post by gvigorus on 2008-10-30
Same here. Can't recover from either Hibernate or Suspend. I'm on Dell Inspiron 4000.

---

### Post by kiddo on 2008-12-14
I think I found the solution, at least for the Inspiron 530 in my case (note: my video card is an Intel GMA 3100 with open source drivers, so if you have an ATI or nVidia thing with the binary drivers, you may need extra hacks). My symptoms were: coming back from suspend, my monitor would scream "please set the resolution to 1920x1200!" in red letters, and I couldn't do anything except reboot the machine. Now, this problem is gone.

I know it sounds crazy and completely unrelated, but **try going into the BIOS, "Integrated devices", and set the SATA setting to "RAID" instead of "IDE".**

And yes, in my case, I'm positive that this setting is exactly the one that fixed the problem; I tested the results empirically/methodically, changing only one thing at a time and rebooting between tries.

What the hell does SATA have to do with my video/monitor not resuming from suspend is beyond me, but it seems to work.

---

