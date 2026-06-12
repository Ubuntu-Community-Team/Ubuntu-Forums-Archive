---
title: "emu10k1 problems"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by scoperesolution on 2005-04-13
I have an Audigy 2 value card and I have been told I need to use emu10k1 as the drivers for it but everytime I try to install emu10k1 it crashes saying it cant find the kernal source.  Has anyone else had this problem with emu10k1?

---

### Post by nautilus on 2005-04-15
shyeah, it doesn't work.

well, i have the audigy2 value, and so far, no dice on getting it working, after two days.

okay, fairly put, i haven't finished compiling the new kernel for it... but still...

---

### Post by dodongo on 2005-04-16
You should download the linux-kernel-source package (I think there's a meta-package that automatically installs the latest version) in Synaptic.  That way, there will be kernel source present against which you can compile the EMU10K1 driver.

And someone who's actually on Ubuntu ATM might check me on this (I'm at work right now) -- but doesn't the EMU10K1 stuff install automatically anyway?  I have an SB Live MP3+ card bordering on ancient, but still has the EMU10k1 chipset, and it worked straight-away.

---

### Post by sofcik on 2005-04-19
I'm new to ubuntu, but have been using gentoo for 2 years. I have sb audigy2 too, and AFAIK our sound cards are supported with 2.6.11 kernels. SBaudigy2 need newest alsa driver, which is present in 2.6.11 kernel, not 2.6.10. Upgrade kernel ( i know there is not official 2.6.11 ubuntu kernel) and sound will be OK!.

---

### Post by scoperesolution on 2005-04-19
After getting the kernal sources and updating some other things I got it to work via apt-get install emu10k1, um there was a site that walked me thought it step by step but its bookmakered on my linux install and at the momment I am programming asm in windows so when I boot back to ubuntu I'll post it.

Scope

---

### Post by merlyn on 2005-04-19
Hi folks, I have been having the same problems, with my Audigy 2 ZS.

There have been instructions on how to get sound working in Ubuntu, in a previous post on this Forum. 

Check out [Hoary Sound Broke]("http://www.ubuntuforums.org/showthread.php?t=21211")

AS for whether installing the 2.6.11 Kernel goes, well I would be willing to give it a try, as even after following the directions in the before mentioned post, I still have to manually turn on the analog/digital output jack each time I boot up.

I find it hard to believe though that installing a later kernel, (to get the latest drivers), is the best answer. After all the same sound card worked perfectly under Ubuntu Warty, and Fedora Core 2 and 3, all shipped with **earlier **kernels.

I would seem that this is a problem with the current release, which to date the Ubuntu people have not fixed, that I am aware of anyway.

Anyway thats my gripe for today. I hope the above link helps out.

Cheers.

---

### Post by sofcik on 2005-04-20
I did what is said in post you gave link to. It works, and i dont have to unmute analog.
Anyways, i've got audigy2 ls, not zs, so maybe only my cards is not supported by official kernels 2.6.10 and older. But of course installing alsa-drivers 1.08 directly from sources works as it should.

---

