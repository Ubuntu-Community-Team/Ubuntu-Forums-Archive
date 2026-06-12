---
title: "Logitech cordless mouse not found in bootup"
date: 2012-08-07
forum: Hardware
---

### Post by RogerDavis on 2012-08-07
It seems that there is a hardware incompatibility?  

Please read below the ------ line first, then the problem.

When I try to run the CD as a test, the mouse is not found. The mouse cursor only appears momentarily as Ubuntu is in process of booting, and I can't move it during that time. The keyboard, which runs off the same USB receiver (Unified) works.

My guess is that Ubuntu is having problems with the "Unified" single receiver for both keyboard and mouse.  This one is different from the usual cordless setup, it can handle up to 6 cordless items. See [http://www.logitech.com/en-us/promotions/6072](http://www.logitech.com/en-us/promotions/6072) . The mouse / keyboard set I have is MK560.

I am using the AMD64 download (VERY confusing that this is also for Intel 64 bit products!?!?!?
-------------------------------------------
I just got a new high power computer and want to confirm which to install of 12.04 - 32 or 64 bit?

Specs:
Intel DZ77BH-55K motherboard
Intel i7 3770 Ivy Bridge CPU at 3.4 GHz
Radeon 7750 1 Gig 800 MHz display card
16 Gig memory
1T hard drive for Ubuntu only

I thought this might be a common question, but a search turned up nothing definitive.

I simply assumed that 64 bit would be the answer, but I see that 32 bit is recommended, and if I select 64 bit, it appears that I'm still only offered 32 bit even though 64 bit is selected - so WHERE can I get a for sure 64 bit version for normal desktop use?

---

### Post by efflandt on 2012-08-09
With 16 GB RAM you would certainly want to run 64-bit because 32-bit cannot address more than about 3 GB, unless using a different pae kernel, which I have never done.

There have been some issues with some Logitech wireless devices, but not all.  My Logitech wireless mouse works flawlessly on my tablet PC or laptop.

But some Ubuntu versions ago (maybe 10.04) something changed in udev that broke certain Logitech things like my diNovo Edge keyboard/mousepad.  I found it very strange that a keyboard/mousepad that works out of the box with CMOS setup, grub, or Windows with no drivers, failed in Ubuntu unless you change something in one of the udev files (which is sort of impossible to do without a different keyboard).

So you might search for "logitech dinovo keyboard" in these forums and see if that fix helps you.  I don't have details off the top of my head.

---

