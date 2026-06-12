---
title: "Unable to install any distro on previously working linux box"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by N00b-un-2 on 2009-08-13
I have an older desktop computer that I am attempting to reinstall linux on.  It has had MULTIPLE distros on it in the past, from Ubuntu Gutsy up til Intrepid, Opensuse 10 and 11, I've tried out Opensolaris and one flavor of BSD on it, so I'm not sure what the issue is.  At one point it actually had Ubuntu 8.04, MacOSX 10.5 (a Hackintosh distro) and a Windows 7 beta build (triple boot).

I just got back from deployment (I'm in the US Navy) and I really wanted to install Linux on it.  I'm not one to throw useful things away simply because they are obsolete, and I had intended to use this computer by hooking it up to my TV as a Media Center PC with Elisa.

The problem is, I've attempted with at least 6 different distros using various releases, kernels, alternate CDs, booting with/without a harddrive attached, swapping ram cards, and no matter what I do, I keep on getting a "low memory corruption" error in verbose mode, or all distros crash pretty much immediately after loading the kernel.

I tried installing Windows 7 RC as well, just to see what would happen and it pops with an input/output error and will not continue, but for some odd reason, Windows XP can install just fine.  What is going on with my computer?

---

### Post by Mark Phelps on 2009-08-13
I've heard of situations where XP would install but newer OSs would not due to failures in the higher memory ranges that XP doesn't access during installation.  But if that were true in your case, I would think that Windows 7 would have encountered the memory problems.

Have you tried booting from an Ubuntu 9.04 CD and running the memory test to at least rule this out?

---

### Post by N00b-un-2 on 2009-08-13
that's just it.  I DID just download a copy of Windows 7 RC and it pops with an I/O error, saying something about being caused by unplugging USB devices while in use and it won't install.
In order, I've tried installing LinuxMint7 and then Ubuntu 9.04, followed by Ubuntu 8.10, 8.04.3, LinuxMint6, Opensuse11.1, and Ubuntu 7.10. EVERY SINGLE ONE freezes before it boots.  I've tried installing in verbose mode and it always crashes giving me the "corrupt low memory" error shortly after booting the kernel and loading a few devices.
I ran a memory test last week and it found like 150+ errors.
I figure that it must be the ram card, so I went out and bought a fresh gig of Kingston DDR1, and I get the SAME exact errors and crashes.
I downloaded a copy of Ubuntu Jaunty Alternative Install disk and was actually successful in installing Linux to the computer, but it would freeze just like the liveCDs shortly after loading the kernel.
What I don't get is why I can't boot the computer into Linux when I've been using this computer primarily as a Linux box for well over 2 years.  The motherboard was replaced less than a year ago, and the computer has been in storage for last eight months while I was deployed, plus it has a brand new ram card so component failure seems unlikely.
Do you think it could be my graphics card?  I have a very cheap nVidia 5700FX card I bought at walmart about a little over a year ago that may have failed onboard ram, but I don't know how I would be able to tell.
well, I'm going to attempt to boot again, this time using the onboard graphics to see if that makes a difference.
Well, I'm rambling so I'll let you know what I find, but any information would be greatly appreciated.

---

### Post by Mark Phelps on 2009-08-14
> **N00b-un-2 said:**
> I've tried installing in verbose mode and it always crashes giving me the "corrupt low memory" error shortly after booting the kernel and loading a few devices.
I ran a memory test last week and it found like 150+ errors.
There you go ... bad memory.
> 
I figure that it must be the ram card, so I went out and bought a fresh gig of Kingston DDR1, and I get the SAME exact errors and crashes.  ... plus it has a brand new ram card so component failure seems unlikely.

IS the motherboard the exact same make and model as the previous?  If not, it may have different default memory timings.  I would go into the BIOS and confirm that there is no overclocking in place, and set your memory to use SPD timings (default).  You might have to experiment with memory timings and voltages to get a stable system.
> 
Do you think it could be my graphics card?  I have a very cheap nVidia 5700FX card I bought at walmart about a little over a year ago that may have failed onboard ram, but I don't know how I would be able to tell.
Sorry, don't know either.  But I think that Nvidia provides a utility to do video memory checking.  But since I don't have an Nivid card, I don't remember it's name.  
> 
well, I'm going to attempt to boot again, this time using the onboard graphics to see if that makes a difference.
Well, I'm rambling so I'll let you know what I find, but any information would be greatly appreciated.
Good idea.

---

### Post by N00b-un-2 on 2009-08-14
Yup.  It was the graphics card.  I unplugged the cheapo GeForce card and booted up using the onboard Intel graphics.  It turned out that the nVidia graphics card had some bad VRAM on it.  It worked like a charm.  After that, I used the Linux System Rescue CD and nuked my HDD so I was completely starting with a clean slate.  I am happy to say that I am now running a fresh install of Linux Mint 7 with Moovida as a mediacenter.

---

