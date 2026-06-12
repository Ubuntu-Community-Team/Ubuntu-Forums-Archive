---
title: "Graphics problem after automatic update"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by wimmelis on 2009-01-15
Dear all,


This issue is a bit split between a pure graphics one and an installation one, but I can choose only one forum ...

Over the last few days, there have been a few automatic updates for my hardy 64-bit. One was a new kernel image, which lead me to a booting problem (which was due to the boot manager). But then yesterday there was another update, and when I then rebooted my machine, I did not get back to my desktop login screen. My video output on the screen looks completely wanky (different squares in different colours etc.). So, I reinstalled completely, and wanted to eliminate the differences. It seems that if I start with e.g. kernel 2.6.24-22 or 2.6.24.23 then my video goes wanky. If I start with the old 2.6.24-16 then it seems to be fine. Since I am running the proprietary drivers for my ATI card (as that is the only way I could get multi-display to work properly) I suspect a software conflict between this graphic driver and one of the most recent updates in combination with the later kernels. 
I had everything working fine with the 2.6.24-22 kernel and the same driver till the beginning of the week, so that is why I expect one of the latest updates, since they were the only change to my computer.  

So, how do I find out which updates were released when ? (Since I have reinstalled my system all updates were installed together, so there is no way to look at something like installation history.)
Anyone else who has similar experience / problem recently ? 
Any proposals for debugging / solving this problem ?


Regards,

WM

---

### Post by wimmelis on 2009-01-16
Dear all, 


Problem solved, seems that the proprietary driver is linked with the kernel modules and this clearly depends on the kernel version, so you need to uninstall the driver before the kernel update, and then reinstall it for the new kernel to get things working again. 


WM

---

### Post by badea on 2009-02-27
Hi!
I have a similar problem. After a system update I'm not able to view the desktop cube any more and scrolling in browser is not smooth. 
I installed the latest ATI drivers (9.2) but that did not solve the problem...
Can you please explain how to uninstall a driver (specifically the video driver) ?

Thanks...

---

### Post by Bones80 on 2009-02-27
I had a similar problem, my wireless worked fine in 24.18 but after upgrading to 24-22 it quit. I don't even get the option of wireless, only wired or point to point.
I made a mistake and used startup manager to cut the number of kernels showing up on boot to 2 and now can't get back to 24-18.
Using 8.04.1 on a Toshiba laptop.

---

### Post by philvdm on 2009-03-07
> **wimmelis said:**
> Dear all, 


Problem solved, seems that the proprietary driver is linked with the kernel modules and this clearly depends on the kernel version, so you need to uninstall the driver before the kernel update, and then reinstall it for the new kernel to get things working again. 


WM

How do you do this?

---

