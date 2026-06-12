---
title: "why isn't this working out of the box?"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by acorrigan on 2005-10-15
Back in March I tried to install Linux on my laptop but gave up since wireless wouldn't work despite this FAQ which directly addresses it:
[http://ubuntuforums.org/showthread.php?t=14490](http://ubuntuforums.org/showthread.php?t=14490)

I downloaded the newest live cd a few days ago, figuring that 7 months later this driver would be part of the release.  My wireless was NOT automatically detected.

Instead of having users look through faqs and manually installing hardware (something I'm terrible at), why isn't it just added to ubuntu so it works automatically?

---

### Post by tseliot on 2005-10-15
[QUOTE=acorrigan]Back in March I tried to install Linux on my laptop but gave up since wireless wouldn't work despite this FAQ which directly addresses it:
[http://ubuntuforums.org/showthread.php?t=14490](http://ubuntuforums.org/showthread.php?t=14490)

I downloaded the newest live cd a few days ago, figuring that 7 months later this driver would be part of the release.  My wireless was NOT automatically detected.

Instead of having users look through faqs and manually installing hardware (something I'm terrible at), why isn't it just added to ubuntu so it works automatically?[/QUOTE]
Open Synaptic/kynaptic and install the "linux-resticted-modules" for your architecture (i386, 686,etc.) in this way you will have the modules you need (I guess).

---

### Post by acorrigan on 2005-10-15
Thank you, I'll try that out.  

I'm still wondering why, if there's a known solution to make this particular piece of hardware work, Ubuntu doesn't detect and and setup the wireless card automatically.

EDIT: I just booted up with my live cd.  386 restricted modules were already installed, but not 686 restricted modules.  Since my wireless isn't already working I'm in a bit of a catch-22 situation.    Anyway, I was also wondering how you knew  orinoco was in this restricted kernel modules package.  It's certainly not self-evident from the name, and I haven't been able to find documentation on what's in the restricted kernel modules packages.

---

