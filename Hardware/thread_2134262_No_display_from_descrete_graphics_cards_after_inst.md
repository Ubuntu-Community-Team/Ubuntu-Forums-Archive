---
title: "No display from descrete graphics cards after install of 12.10"
date: 2013-04-10
forum: Hardware
---

### Post by jeliocranch on 2013-04-10
Its a long story why I'm on a fresh install of 12.10, but suffice it to say I never found a successful method for installing nvidia drivers in my previous 12.10 install.  My system is Nvidia 550TI, ASrock extreme4 socket 1155, Intel i5-3570K, Seasonic x-650 platinum PSU, and had been running successfully with nouveau for a month, and prior with an ATI Radeon 4850 since November 2012.

After many hours and successful repairs and unsuccessful re-attempts, I gave up and re-installed 12.04.1 (64 bit) from alternate media.  Graphics, while text only or n-curses style windows, worked during install, but nothing after grub splash (the big ugly one, not higher res).  Motherboard didn't show errors, just nothing.

I then tried installing 12.10 (64 bit) from live media.  Again, during install the Nvidia graphics were working, running both of my monitors.  After install, it continued to work for three reboots (the driver is/was listed as "unknown" rather than nouveau), then the same as before: nothing.

I pulled the card and checked PCI-Express power: 12.2V
I tried onboard graphics (intel 4000 HD), works (interestingly, the BIOS reset itself to PCI-Express as default graphics even still)!

I re-inserted the 4850 card, still nothing.
booted perfectly to liveUSB with 4850 however, and same with another attempt at Nvidia 550 Ti, so I'm pretty sure its the OS. not the motherboard, PSU or graphics cards.

I haven't had to do much to make graphics work in Ubuntu, using since 9.04.  I'm frustrated...
thanks in advance

---

### Post by jeliocranch on 2013-04-11
Bump? or did I post in the wrong spot?

---

### Post by Mark Phelps on 2013-04-11
> **jeliocranch said:**
> Bump? or did I post in the wrong spot?

Your title tells us little about what combination of graphics you have on your PC.  If you have some form of Hybrid Graphics (two chipsets, one on board, the second with a card) ... then before you continue complaining, you should read the details in the link:

[https://wiki.archlinux.org/index.php/Hybrid_graphics]("https://wiki.archlinux.org/index.php/Hybrid_graphics")

The problem you have is COMMON to Linux -- and not easily solved in Linux.

---

### Post by jeliocranch on 2013-04-12
I'm sorry.  I didn't mean to complain.  I saw it was viewed a lot without any reply even to say "we need more info".  I thought I might have posted in the wrong place.  Again, I'm sorry if I was rude.

My system having problems is not using Hybrid graphics.  It is: 
CPU: Intel core i5-3570K
Mobo: ASRock Extreme4 
16 GB DDR3
Nvidia GTX 550Ti graphics card

When it was working, it was *NOT* using the built in graphics, only the Nvidia card.
When using any live media, the Nvidia card works fine.
On the third boot after completing the install, no graphics.
Removing Nvidia card, replacing with a known working card: no graphics.
Removing all descrete cards, using graphics on the CPU: I get graphics.

There are no proprietary drivers installed that I know of.

---

