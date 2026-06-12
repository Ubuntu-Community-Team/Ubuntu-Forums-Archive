---
title: "Sleep issues—seriously need help"
date: 2010-01-16
forum: Hardware
---

### Post by Firepowerforfreedom on 2010-01-16
First off, I'm loving Linux. It's responsible for turning the family desktop from a piece of junk to a powerhouse, and I'm actually going to help my brother set up UNR when he gets his Asus Eee PC next month (I could never convince him to use Mac OS X, but he seems to like the looks of UNR on our Pavilion desktop).
  I'm setting up a dual-boot system (I've already got the partitions made and Mac OS X is on the first one), and I'm trying to find the best variant for my nearly ten-year-old PowerBook G3 Pismo. If you need the specs, here they are:

—500 MHz PowerPC 750 [aka G3], 1 MB L2 cache 
—512 MB 100MHz SO-DIMM RAM in two 256 MB cards
—ATI RAGE Mobility M3 with 8 MB VRAM
—2 media/battery bays, sometimes with both batteries in, other times with 1 battery and a DVD-ROM module
—14.1" TFT flatscreen display

I've tried Kubuntu 8.04, 9.04, and 9.10; I've tried Debian with GNOME and KDE 3.5; I've tried Xubuntu 9.04, 9.10, and 10.04 alpha 1; I've tried Ubuntu 8.04 and 9.04. Of these, only one has ever produced fairly consistent results when it comes to suspending-to-ram, and that would be Kubuntu 9.04 (oddly enough).
  The point is, this laptop is mobile; it spends most of the day unplugged (8 hours of battery life, baby!), and it needs to be able to suspend when I close the lid and resume when I open it. 
  My usual symptoms are these:
  1. The laptop does not suspend at all; screen goes black; backlight stays on; hard drive still spinning
  2. The laptop tries to suspend; screen goes black; backlight turns off; hard drive still spinning
  3. The laptop almost suspends; screen goes black; backlight turns off; hard drive stops spinning; faint squeal begins emitting from somewhere inside; sleep LED does not turn on (should flash)
  4. And, just to demonstrate what this thing does when it does suspend (rarely): little bit of read/write action on the HD, followed by near instant spin-down; blacklight flips off; sleep LED glows dimly for a moment, then starts to cycle low-high (all Apple computers do this since 2000, I think); no noise. This all takes about five seconds.

  This may not be limited to PowerPC processors or Apple laptops; I'm hearing reports especially from IBM/Lenovo users about suspend issues. Any advice (I don't really like Kubuntu 9.04—the panel inverts colors on me and moves slow)?

---

### Post by lukeiamyourfather on 2010-01-16
Probably not the answer you're looking for but the hardware is so old and rare that its probably difficult to develop and maintain (because nobody has one to test on). If a slightly older version of Ubuntu (or any other Linux) works better then I'd stick with that if it were me. Someone that's more familiar with the inner workings of suspend and power management in Linux might be able to help more, but a more focused forum would be the place to find those people instead of a general forum like this one. Cheers!

---

