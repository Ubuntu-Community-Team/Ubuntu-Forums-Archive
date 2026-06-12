---
title: "I really want ubuntu to work on my GX620"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by brimbleshoes on 2006-07-12
At work they gave me a GX620.  I have tried all kinds of things to get it to work with Dapper -- it all comes down to one issue; applications just shutdown randomly.  I'm in gnome and I have any application open and then it just disappears without warning.  The JVM, file browser, text editor, etc.  Sometimes I get a window that tell me it shut down and that I can file a bug.  I don't know enough about it to submit a bug.  It doesn't matter what I'm doing, stuff just shuts down.  I left the Gnome System Monitor up, once for about 15 mins, and another after an hour.  Both times it just shuts off randomly.  I have tried using vesa, radeon, and fglrx in xorg.conf.  I have tried combo mode on the sata controller.  Used the 686 kernel, with ht=on in GRUB.  here are the boxes stats:

PENTIUM 4 PRESCOTT DT, 630, 3.0, LGA, R0 with HT turned on
1G RAM
80Gig SATA drive
945G intel chipset
ATI GRAPHICS PCIE, 128M, X600, OUGA3, LOOP

I'm so frustrated! I've tried straight Debian, CentOS, and trying to get Gentoo to work also.  Anyone else get a similar GX620 to work with Dapper!?

](*,) 

-- Tom

---

### Post by mcallihan on 2006-07-12
I've got a GX620 running rock solid. only difference i see you have is the ATI card. I'm running an Nvidia 7600 GT. Got TwinView XGL/Compiz running also. Have you ran the Dell diagnostic disk to see if you got a hardware issue?

---

### Post by mcallihan on 2006-07-12
More info: I'm using kernel 2.6.15-26-386. Where did you get the 686 kernel?

---

### Post by brimbleshoes on 2006-07-13
I got 686 off of syanptic.  

It didn't seem to make a difference though.  I was running 386 with problems too.  Sounds like its an ATI thing.  

You have the 945G chipset?  And you running HT on the processor also?

---

### Post by mcallihan on 2006-07-13
i just got the 686 kernel also off of synaptic and have no issues.
945 chipset and HT proc. I don't have ht=on in my grub but when i go into the system monitor i see both procs. Definately sounds like an issue with ATI. do you have issues with just using the internal video card?

---

### Post by brimbleshoes on 2006-08-10
FYI --
It looks like I had a defective box.  I now have a new box with the same config, no problems at all.  

Therefore, ubuntu does work with the Dell Optiplex GX620.

I have the radeon X600 -- use "radeon" or "fglrx" in xorg.conf for the video driver.

---

### Post by homegrown on 2006-09-24
Hi there -- I've been running dapper on a GX620 for quite a while now. I've just updated the BIOS version from 06 to 08 & my previous USB & Disk issues seem to have dissapeared.

Not sure if it'll fix your problem, but well worth doing!

---

