---
title: "Jaunty -&gt; Karmic upgrade"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by NPH0RM on 2009-11-03
Hi, i just upgraded for jaunty to karmic. Installation went well until reboot: screen kept black!
I restarted my computer in kernel 2.6.31 recovery mode and got finally to the console. login worked. startx didn't. screen kept black again.
Again i restarted with kernel 2.6.28. login worked, but i can't hear a sound and my touchpad doesn't work. that's lame. waiting for the next upgrade with better karma...

I am using Samsung R41 notebook with ATI Radeon XPress200M.

---

### Post by pi4r0n on 2009-11-03
And this is your problem mate :(

> **NPH0RM said:**
> ATI Radeon XPress200M.

You can try 2 things:

[LIST=1]
[*]Install clean Ubuntu system from DVD. This help few on my friends 
[*]Update Drivers in Ubuntu
[/LIST]

Cheers

pi4r0n

---

### Post by NPH0RM on 2009-11-03
lol, that shouldn't be the problem, it worked with jaunty and is working with kernel 9.6.28

---

### Post by peakpc on 2009-11-07
I have a laptop (Compaq V5000) with a ATI xpress 200m. I did not upgrade but, started fresh 32bit... video does work with kernel 2.6.31-14, even Compiz and video seem to run smoother than in 9.04 however the kernel mode-setting ATI drivers seem to be still a work in progress as if I switch users, suspend or hibernate it resumes to a black (blank) screen with no recourse but to reset. :( I hope that there is enough of us complaining to make this a priority to fix soon.

---

### Post by pi4r0n on 2009-11-09
> **peakpc said:**
> the kernel mode-setting ATI drivers seem to be still a work in progress as if I switch users, suspend or hibernate it resumes to a black (blank) screen with no recourse but to reset. :(


:lolflag: I got **ATI Mobility Radeon HD 4530 Series (512 MB)** and I have got the same problem like you **peakpc** (with hibernate or resumes modes).

Ta

pi4r0n

---

### Post by crashflow on 2009-11-09
I also have a Samsung R41 laptop with an ATI X 200m. When I try to boot the Kubuntu 9.10 Live CD, the screen just remains black.

This is not an ubuntu-specific problem I think, since my Fedora 12 installation based on rawhide also ceased to work normally after installing the latest updates. I can only access the system with nomodeset on runlevel 3 - When starting X, the system hangs instantly.

When I find the time, I will try again and file a proper bug report - but basically ATI X 200m support seems to be broken completely.

Regards
crashflow

---

### Post by peakpc on 2009-11-09
The person most responsible for the Kernel mode-setting ATI driver is  Jerome Glisse acording to this [article]("http://www.linux.com/archive/feature/118724") and it would seem that he is working on this issue as it is on his "to do" list, however, maybe a few nicely written words of encouragement might help. Then of course it has to be incorporated into the next Kernel update. 

Patience is a virtue I'm still working on.

---

### Post by bertmanphx on 2009-11-11
Peak,
I do not know if this is related, but the symptoms seem very similar.  See the [posts here]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1307618")

I've got the same video card, and when resuming from suspend or hibernate, bet the dreaded black screen.

bertmanphx

---

### Post by peakpc on 2009-11-22
Yes I have posted on that thread as well.  I am thinking that kernel 2.6.32 might have the solution. hopefully it will come out in December so we can give it a try.

---

### Post by bertmanphx on 2009-11-22
Hello,
Actually, I solved this issue for me by installing the xorg ATI and radeon driver from the Jaunty repository.

bertmanphx

---

### Post by LoloftheRings on 2009-11-22
It actually works for me with the same kernel as ubuntu 9.10 (running arch linux). I just installed the driver from amd.com (not recommended, only if you really know what you're doing) and it all works.

Ati drivers do not support every kernel, and the drivers are often crappy. Nvidia is a better bet.
Ati works, but not as it should be.

---

