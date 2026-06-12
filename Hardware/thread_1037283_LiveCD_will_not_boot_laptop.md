---
title: "LiveCD will not boot laptop"
date: 2009-01-11
forum: Hardware
---

### Post by figgles on 2009-01-11
I have an old HP Pavilion N5450 laptop: a Celeron 850 MHz with 256 MB RAM.

Here's the rub: I have booted and installed Puppy Linux 4.2 on it, no problems. However, the same system will freeze at startup with ubuntu LiveCD and Intrepid. It stops on "mounting root file systems" I've tried the various boot parameter settings: noacpi, root=/dev/sda2 (the hd as puppy sees it) xforcevesa, I don't know what else to try.

What else can I try to boot with the ubuntu live CD?

---

### Post by ajcham on 2009-01-11
> **figgles said:**
> I have an old HP Pavilion N5450 laptop: a Celeron 850 MHz with **[COLOR="Red"]256 MB RAM[/COLOR]**.

The Intrepid LiveCD requires 384MB. If you wanted to install it, 256MB would be sufficient for the alternate CD, but it might not run that well.

---

### Post by figgles on 2009-01-11
> **ajcham said:**
> The Intrepid LiveCD requires 384MB. If you wanted to install it, 256MB would be sufficient for the alternate CD, but it might not run that well.Yea, that's the suggested minimum but I'm over the required minimum. (64 mb) But I suspect that's not the problem at this point of the boot.

---

### Post by ajcham on 2009-01-11
> **figgles said:**
> Yea, that's the suggested minimum but I'm over the required minimum. (64 mb) But I suspect that's not the problem at this point of the boot.
64MB is the required minimum for an *installed* Ubuntu (with caveats).  You are 128MB below the required minimum for the LiveCD.

Whilst you may be correct that it is not lack of memory causing problems so early in the boot process, it will cause problems later so probably isn't worth persevering with.

---

### Post by figgles on 2009-01-11
> **ajcham said:**
> 64MB is the required minimum for an *installed* Ubuntu, and even then there are a number of caveats.  You are 128MB below the required minimum for the LiveCD.

Whilst you may be correct that it is not lack of memory causing problems so early in the boot process, it will cause problems later so probably isn't worth persevering with. Hmmm! Interesting. Puppy Linux runs, OK, on it -- performance is good, (for what it is) but it "feels" quite the younger sibling compared to richer feature set offered by ubuntu. Yes, I'm aware of the computational overhead of an expanded feature set, but I wanted to check it out, given the price point.

I guess I'll just leave puppy on it, then.

Thanks!

---

### Post by ajcham on 2009-01-11
> **figgles said:**
> Hmmm! Interesting. Puppy Linux runs, OK, on it -- performance is good, (for what it is) but it "feels" quite the younger sibling compared to richer feature set offered by ubuntu. Yes, I'm aware of the computational overhead of an expanded feature set, but I wanted to check it out, given the price point.

I guess I'll just leave puppy on it, then.

Thanks!

Puppy Linux is a completely different animal from Ubuntu.  It is specifically designed to be run on low-end hardware - you could run Puppy quite comfortably with just 32MB of memory.  256MB is enough to allow Puppy to run entirely in RAM.

---

