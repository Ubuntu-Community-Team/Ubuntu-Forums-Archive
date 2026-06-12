---
title: "Acer Laptop with Nvidia Flickers and Overheats"
date: 2009-10-18
forum: Hardware
---

### Post by steve8track on 2009-10-18
I hope this is the right forum.

My screen has been flickering more and more.  It's not the entire screen, but only certain shades of dark will flicker with little blue-green lines.  For example, the top of wikipedia.org where the background image is flickers.  I thought it might be an NVidia driver problem, but I've seen the same flicker in Windows once (I don't boot into Windows very often, so I don't see it there as much).  One day it flickered red instead during the boot screens even before grub had loaded.  It hasn't done that since, but this makes me think that my problems are probably hardware related rather than software.

I have an Acer Aspire 7720-6152 with a NVidia Geforce 8600M GT.  It's about 1 year old.  I've wiped my computer clean from Ubuntu Studio 64-bit Hardy and Windows XP 64-bit.  I now run only Ubuntu 64-bit Jaunty.  All of the OSs have had the flicker.

I've heard that my graphics card has a bad history of failure, so I'm wondering if it's possible to replace it, or if there is a work-around if it is something wrong with my hardware.

I'm also having overheating problems.  When I first got the laptop, I had a similar problem and I thought I had fixed something with ACPI before, but it's been a while and I can't remember.  It overheats way easier than it used to.  I used to encode videos for a few hours without it overheating, and now it overheats after only encoding for 20 minutes or so.  It even overheated today without my encoding anything.  It just turns off immediately, which is why I think it's overheating.  Then when I try booting it, during the boot process it will turn off before getting to gdm.

dmesg returns: "APIC error on CPU0: 40(40)"

These problems are really frustrating to me, so I appreciate the help.  If it turns out to be the graphics card it will be ironic since that's the main reason why I bought this thing.  Let me know if you need any more details.

---

### Post by viper250 on 2009-10-18
overheating problems are usually caused by dust build up on the cpu heatsink and can also show up as video problems _use canned air to clear the dust out _
**do not use an air compressor though because possible moisture in the compressed air can cause a tremendous static charge to build up **

---

### Post by steve8track on 2009-10-20
Interesting.  Thanks for the advice!  I hope it works.  That would be awesome if that's all it is since it seems so simple :-)

---

### Post by Dark_Stang on 2009-10-20
> **viper250 said:**
> **do not use an air compressor though because possible moisture in the compressed air can cause a tremendous static charge to build up **
And many air compressors run at 100 psi, so if you don't have a regulator that will definitely break some fans.

---

### Post by pupfishdesign on 2009-10-31
I have an Acer Aspire 7720.  the generic kernels that delivered with (and were upgraded under) 9.04 managed my two cpu fans properly.

The kernel no longer controls CPU fans under 9.10.

This is an urgent problem.  Until we find a solution, 9.10 has bricked this class of laptop.

If anybody can help me identify what I need to look for in the kernel to fix this, I would be very grateful.

As an aside, solving this on my machine will be tricky -- a compile of more than just a few minutes will overheat my CPUs to the point where the thermal safety (at the board???? or BIOS??? level) will instantly shut the system down.  If I have to recompile a kernel on this machine, I will have to temporarily press a fan onto my chasis fan and hope that moves enough air across the CPUs to do the job!

Insights?  Experiences?

Help...

---

### Post by steve8track on 2009-11-19
I've had this overheating problem on both 9.10 and 9.04 I think, although 9.04 was the rc (or is it called rt) kernel.  You could try a chill pad while you are compiling.  Or you could just install 9.04 again if you don't mind being out of date for a while.  I'm not sure what else to suggest unless there is a software solution like a patch you could keep your eyes peeled for.  Maybe the backport and pre-release repositories could help?

As for my problem, I dusted my laptop out, but the problem persists.  It seemed better for a short while and I started using a chill pad, but after a few weeks it came back and it could be that I wasn't using my laptop for anything that heated up the graphics card for a while.  After doing graphically intensive work instead of just CPU intensive, the flicker came back.  I think I'll need to replace the graphics card, but I'm not sure where you can buy cards for laptops.  Newegg seems to only have graphics cards for desktops.  Also, I do know the graphics card is removable because I removed it while dusting.

Thanks for the help though, and good luck with your overheating problem.

---

