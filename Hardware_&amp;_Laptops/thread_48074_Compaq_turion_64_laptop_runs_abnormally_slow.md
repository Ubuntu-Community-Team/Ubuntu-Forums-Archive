---
title: "Compaq turion 64 laptop runs abnormally slow"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by atrus325 on 2005-07-11
I'd love to run Ubuntu on my laptop (Turion 64 chip with 512mb ram), but I'm running into problems with X running obscenely slow. 

I mean really slow.

Everything is fine from the command line.  Boot up is as fast as ever, but the minute I enter X, problems begin.  At first, I solved a problem with lock-ups by changing the video driver from ati to vesa in xorg.conf.  The laptop does have an ATI card onboard, but I knew from the beginning there were steps I was going to have to take in order to get that working correctly.  However, that didn't fix the slowness.  I mean, it feels downright lethargic, and frankly, I'm at a loss why it would be doing this.

Any ideas?  Has anyone experienced anything like this before?  My hardware works fine.  I checked it out thoroughly once I started having these problems.

Thanks in advance for your suggestions,

J.

---

### Post by brim4brim on 2005-07-11
[QUOTE=atrus325]I'd love to run Ubuntu on my laptop (Turion 64 chip with 512mb ram), but I'm running into problems with X running obscenely slow. 

I mean really slow.

Everything is fine from the command line.  Boot up is as fast as ever, but the minute I enter X, problems begin.  At first, I solved a problem with lock-ups by changing the video driver from ati to vesa in xorg.conf.  The laptop does have an ATI card onboard, but I knew from the beginning there were steps I was going to have to take in order to get that working correctly.  However, that didn't fix the slowness.  I mean, it feels downright lethargic, and frankly, I'm at a loss why it would be doing this.

Any ideas?  Has anyone experienced anything like this before?  My hardware works fine.  I checked it out thoroughly once I started having these problems.

Thanks in advance for your suggestions,

J.[/QUOTE]
 The vesa card isn't developed by ATI and won't take full advantage of your graphics cards capabilities from what I've seen I have the same problem.  ATI don't offer proper drivers for their laptops for Linux I installed the one on their site and it doesn't work with the X600 Mobile card.

I think all you can do is what I did and send an email to ATI and ask them to start writing a driver that supports Linux for your card.

---

### Post by atrus325 on 2005-07-11
That's a good idea.  Those kids do need some motivation (I SOOOOO wish this laptop had a nvidia chip).

Still though, the vesa driver does work plenty fast on Suse, Slamd64, Mandrake, Fedora, and a half dozen others that I've tried.  I just like Ubuntu and Gentoo better.  I'll just play with Gentoo for now until the Breezy Badger, I guess, and hope the Badger works better.

Unless there are other ideas out there..

J.

---

