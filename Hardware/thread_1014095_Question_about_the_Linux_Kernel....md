---
title: "Question about the Linux Kernel..."
date: 2008-12-17
forum: Hardware
---

### Post by Roasted on 2008-12-17
I'm just curious, how far ahead are developers with making newer editions of the Linux Kernel from the stable release? I mean, didn't 2.6.27 just come out?

Long story short, I'm running CloneZilla LiveCD at work for 1 on 1 cloning backups for systems that crash or whatever. I keep a library of images on my external HDD and when a system drive goes bad, I pop a new one in, pull the image up on the external HDD and let CloneZilla LiveCD do its thing.

Problem is, I couldn't use it on these Dells. A Dell? Being stubborn? COULDN'T BE! :lolflag: Anyway so it wouldn't recognize the hardware. Turns out .27 kernel doesn't play nicely with the SATA controller that these Dells were using (pretty darn new Optiplex 740's).

Someone at the CloneZilla forums was kind enough to upload an experimental version of CloneZilla (for stable release, eventually) with the upcoming Linux Kernel of 2.6.28.

BAM. .28 works! .27 doesn't... yet .27 is brand new. Isn't it?

So I'm just wondering how in the world the time map pans out here? Can anybody fill in the blanks for me? Thanks!

---

### Post by Ayuthia on 2008-12-17
There isn't really a timeline for when a kernel is released.  If you are curious about which is the most recent stable kernel you can check it out at:
[http://kernel.org/](http://kernel.org/)

It lists out the current kernel version and the release candidate version for the next kernel.

As of recent, it seems that they are getting out two new relases (the 2.6.xx release) about every six months, but that is not the expectation.  They are just released when they are ready.

---

### Post by Roasted on 2008-12-17
I see. So the guy from the CloneZilla forums probably acquired the .28 kernel from here and compiled everything to the LiveCD I downloaded. Interesting stuff!

---

