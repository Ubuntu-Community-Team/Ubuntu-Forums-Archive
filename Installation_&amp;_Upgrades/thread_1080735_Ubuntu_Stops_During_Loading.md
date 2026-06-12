---
title: "Ubuntu Stops During Loading"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by mikedmor on 2009-02-25
I tried installing ubuntu 8.10 32bit on my pc and when ever the os was loading it would just stop (not freeze). I turned off the flash and every time it seems to be at something different.

I was told by another forums that i should probably try 64bit and see if that helps but it still just stops during the load. Now with the 64bit install and splash off i can see where it is stopping but its still at random positions.

Right now it is froze at:
ath9k 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19

But as i said it stops at random positions. Some occasions it does seems to start though. Also these stops occur after it post:
* Loading hardware drivers...

Any ideas? here are my pc specs:

Processor:  AMD Phenom(tm) 9950 Quad-Core Processor (4 CPUs), ~2.6GHz
Memory: 6.00 GB RAM
Hard Drive: Western Digital Caviar WD10000LSRTL 1 TB Internal SATA Hard Drive
Video Card: NVIDIA GeForce 9600 GT
Motherboard: MSI K9N SLI-F V.2 (MS-7390-010)

---

### Post by mikedmor on 2009-02-25
Ok Actually i figured out that the bios on my motherboard was set to increase (overclock) my processor. So by removing that setting it works just fine!

Except for a problem that i was having on 32bit that i thought i knew how to fix but it doesn't work. 

I was having problems with my wireless card, it would cause ubuntu to freeze when ever it was being used, no problem if i dissabled networking. But i fixed it by installing a program in the 32bit called Windows Wireless Drivers (or something along the lines of that). And it seems that this program isnt available for the 64bit version. So i tried using ndiswrapper to get the drivers installed but still no luck. Any ideas?

---

### Post by mikedmor on 2009-02-25
wow well these forums are pretty much useless. figured it out on my own. turns out that the tool was already in the system.

thanks for no help guys!

---

