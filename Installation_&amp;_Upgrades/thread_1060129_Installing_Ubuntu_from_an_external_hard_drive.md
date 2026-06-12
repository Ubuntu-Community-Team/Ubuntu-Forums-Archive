---
title: "Installing Ubuntu from an external hard drive?"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by Veteropinguis on 2009-02-04
This is my third or fourth time trying to dual-boot on the same machine. Each time I have been left with no ability to boot in to either OS. I tried to restore a missing boot kernel, but Windows isn't finding my partition. Ubuntu doesn't load...well, it did one time, but I have no idea what happened. I left the room for a few minutes and when I came back, somehow Ubuntu had booted. However, upon rebooting, everything went to hell. As far as I can tell, though, the issue could very well be with my CD drive. No problem, right? Just install from a flash drive.

Well...the only flash drive I can get my hands on is 512mb, and I don't have another optical drive lying around. I do have an 80 GB external hard drive. Could I use that to install Ubuntu to my machine?

I was on the site for Damn Small Linux and read that it can be expanded in to a Debian install. If that's the case, is there a way for me to install Ubuntu from the command line in Debian?

---

### Post by Jesper-L on 2009-02-04
You can install both TO it and FROM it. I suggest taking a look at [unetbootin]("http://lubi.sourceforge.net/unetbootin.html") which you can use to make your hd work as a cd-rom drive loaded with ubuntu - so to speak.

Your PC must be able to boot from USB hd's though.

This advice is based on the assumption that you are in windows now. Ubuntu itself has the ability to create live-cd's of almost any media

---

