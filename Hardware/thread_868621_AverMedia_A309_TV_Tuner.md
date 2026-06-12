---
title: "AverMedia A309 TV Tuner"
date: 2008-07-24
forum: Hardware
---

### Post by coolen on 2008-07-24
My laptop, Acer Aspire 6920, came with Vista Home Ultimate. I scrapped that recently, and am now dual-booting XP Pro and Ubuntu.

Unfortunately, the TV Tuner doesn't seem to work in either. I'm not really surprised about Ubuntu, but I found the driver for XP, and Device Manager recognises it.

When I googled the problem, I saw an article claiming that AverMedia were producing drivers for Linux, and seemed rather dedicated to that. It was an old article, but I'm wondering if anyone knows if it's possible to get it working in Linux, or how to get it working in Windows, or both. I've tried a dozen different programs on Windows to try to get something from it, and at best, they find my webcam...

---

### Post by prshah on 2008-07-24
> **coolen said:**
> 
Unfortunately, the TV Tuner doesn't seem to work in either. 

Unfortunately, some (cheap) TV tuners seem to work only with the OEM programs, and not with Windows Media Center and/or Ubuntu.

I have a Mercury TV tuner with Philips saa7134 chipset, that works (used to) in  (ex-) Windows, but only with the custom program that comes from the driver CD. A quick glance at the Windows event viewer (start-run-eventvwr.msc) revealed errors similar to "OEM TV Tuner malfunction" (words to that effect). If you have the same error, you probably have the same problem.

I have got it working in ubuntu, after a fashion; it works only in tv time, and only black/white. The radio function doesn't work (no sound, tuning, etc).

Can you check eventvwr in Windows Xp and see if you get a similar error message?

---

### Post by coolen on 2008-07-24
Not sure exactly where to look, but I'm not seeing anything like that.

---

