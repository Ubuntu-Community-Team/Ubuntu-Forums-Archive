---
title: "GPU using too much power"
date: 2015-04-18
forum: Hardware
---

### Post by lwfx on 2015-04-18
I currently have an R9 290 and am having problems with power usage in Ubuntu.  On Windows, my machine will be pulling around 75-80watts from the wall at idle and stay at around 35c.  When I switch over to Ubuntu the power usage is 140-200watts depending if I have a program open and idles at 53c with the fan blowing at a decent volume.  I have used fanless GPUs in the past (They always were running hot in Ubuntu though ) but since now I have the louder fans, I plugged in my Killawatt to check the power draw and was surprised. With the proprietary drivers it reduces the draw a little bit, but is still at about 120-180w. Is there something that I should be doing to reduce power? I have tried 14.04, 14.10 and 15.04; 15.04 works the best out of the bunch but have been seen drawing of over 200w while using a simple text editor or having a browser open. Is there some best practice of taking care of this?

---

### Post by weatherman2 on 2015-04-18
Confirm that the problem is really the graphics card by trying another graphics card (or use integrated graphics temporarily, if your motherboard has them) and then measure the power use Windows vs. Linux again.  If the idle power is about the same without the R9 290 then you know for sure it's the graphics card.

If it really is the graphics card drawing the extra power, try an AMD support forum and try the latest driver:

[http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/latest-linux-beta-driver.aspx)

If it's not the graphics card, look for another solution.  However, if you are saying idle temperature of the CPU is 53C in Ubuntu but 35C in Windows, then it probably has nothing to do with the graphics card.   So - then what motherboard are you using?  Or is 53C / 35 C the idle temperatures of the GPU?

---

### Post by lwfx on 2015-04-18
I am talking about the GPU, as problems seem to always stem from there. When I installed Ubuntu on my laptop some time ago the battery life was halved and got hot during normal usage so I figure there has to be some settings some where that involved some sort of regulation; allthough looking around online it seems people are saying that Ubuntu is a power hog, so maybe nothing can be done about it.

---

### Post by weatherman2 on 2015-04-18
It depends largely on the hardware and how well it is supported in the kernel.  It has not been a general trend for me with Ubuntu that it always uses more power than Windows.  I have a watt meter, too.  My current netbook (used every day) uses the same idle power with Ubuntu 12.04 as with Windows 8.  I test almost every new Ubuntu install I do with a watt meter.

I have seen that the AMD CPU-based hardware I've used tends to use more power in Linux than Intel CPU-based hardware, but I haven't used too many AMD CPUs.  So I can't claim it is generally true.  Once, I inherited a  an AMD Athlon-based laptop that used about 50% more idle power than in Windows Vista.  I could not find any obvious ways to tune power use.  Since it wasn't a laptop I was going to use anyway, I left Vista on it and gave it away.  I stick to hardware (usually Intel) that is well supported in Linux and does not use more power than in Windows.  Other machines I've used with Intel CPUs have not needed any tweaking to get power use down.

---

### Post by lwfx on 2015-04-18
Yeah, this PC is an i5-2500k. Thanks for the replies, I'll keep looking around.

---

### Post by QIII on 2015-04-18
Hello!

If you are using the open source driver, the power management part has gotten much better in the last couple of years.  However, this is one area where the proprietary driver still does a much superior job.  My R9 290X idles around 37C at 20C ambient -- and runs cooler under load with the proprietary driver than you are seeing at idle..  That indicates lower wattage.

Your GPU should certainly not be pulling that sort of wattage.  I have a load indicator in my conky, and under normal casual usage my GPU bumps back and forth between 0 and 3% load until I play a movie or do something similar.

I'm not at home with my notes to give you examples of the commands, but you can monitor load and temperature using the command line Linux Overdrive utility.

---

### Post by lwfx on 2015-04-18
I appreciate the info. I came across a thread discussing how 14.04.2 was having issues with the driver, so I installed 14.04.1 with the proprietary drivers and everything worked great! temps down to 40c idle and wattage down to 95-100w. Then it asked for an update and when I restarted, jumped back to 155-180w with a +50c temp and sketchy performance on some programs. Do you know of any method to stick with 14.04.1 while still getting some basic updates for security/programs? I don't exactly know what comes with 14.04.2 that makes it all go crazy.

---

### Post by weatherman2 on 2015-04-18
Did you try to download and the driver from AMD directly from their website, in 14.04.2?

---

### Post by QIII on 2015-04-18
Installing the driver directly from the AMD website can have three distinct drawbacks if not done in a particular manner -- that is if one does not create a .deb package with it.

1.  When the shell script (.sh file) is used directly, the driver must be uninstalled and then reinstalled using the .sh when there is a kernel update.  

2.  If there were ever a security update passed down through the Ubuntu repos, you'd never get it.

3.  It has not been tested specifically for trouble-free installation by the packagers at Canonical.

Unless there is some specific functionality that comes out with the AMD driver outside of the Ubuntu release schedule and you simply cannot live without it, I suggest that using the package from the Ubuntu repo with each release every six months is liable to be less fraught with significant emotional events.

The driver that comes out with each semi-annual release of Ubuntu is the same driver as the one released by AMD that month.  Canonical does not (an cannot) modify the proprietary driver itself.  They do package it in such a manner as to make sure it works -- and that allows you to update your kernel and have the driver module re-insterted.

So Canonical always has in its repo the actual driver that was released by AMD in April or October of the release year.  If you can live without each monthly AMD release (which is pretty much the case), then doing things the easy way makes more sense.

@lwfx:  Did you install the driver from the repo?  Was your system upgraded to 14.04.2?

---

### Post by lwfx on 2015-04-19
I installed the driver through the software center/additional hardware (fglrx and also tried fglrx-updates), which works good on 14.04.1. But upgrading to 14.04.2 breaks it and also installing it while on 14.04.2 breaks the same way.
In addition, on 14.04.2 I tried the driver directly from AMD's site, both the 'Linux' driver and the Ubuntu specific, both which caused a login loop.

---

### Post by QIII on 2015-04-20
There is a bug in the installer for 14.04.2 and the fix may not yet be in the main trusty repo.  See my post #77 in the bug report for how to install it from trusty-proposed.[SIZE=2] 

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)[/SIZE]

---

### Post by lwfx on 2015-04-20
You did it! Temps down, wattage down, performance back up, thanks a ton!!

---

### Post by QIII on 2015-04-20
I didn't do much more than report a bug and test the fix...

---

