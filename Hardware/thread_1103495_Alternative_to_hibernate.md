---
title: "Alternative to hibernate?"
date: 2009-03-22
forum: Hardware
---

### Post by outofsync on 2009-03-22
Brief explanation:

Is there some alternative to hibernate, so that I could save to disk the exact memory dump of a running app, and restore the dump when I reboot? (my interest on hibernate isn't booting time, but keeping my workspace in the same status were it was left).


Longer explanation follows:

I just bought an Acer Aspire 6935G, and installed 8.10 (64 bit version), dual boot with Vista.

I must say that I found more issues with 8.10 on this Acer than with previous Ubuntu versions on other Acer laptops that I installed and used in the past, but anyway I'm happy with it (the tools I use work fine) and that's not the point.

The point is that hibernate is more broken than it used to be: In other Acer laptops with older Ubuntu versions, I was able to hibernate (although it sometimes failed, but most of the times it worked). In 8.10 it's really broken, and even dangerous: after hibernation, the laptop won't boot until you unplug and plug it again, and even then when it boots, the keyboard doesn't work at all, so you've to reboot, and then everything works fine.

I've read that hibernation is quite hardware-dependent, but however I tend to believe there should be a soft alternative that just dumps the full memory of some running apps before you reboot, and recovers it after booting... this should be hardware-independent.

Maybe the user could be allowed to select which apps to hibernate (for example: "on next reboot, hibernate Gimp").

Does anything like this exist already?

Thanks!!

---

### Post by mtbsoft on 2009-03-22
My best suggestion would be to install some form of Virtual-ware and run the apps you wish to hibernate in VMs.  True, it means you have the overhead of running two copies of the o/s but if you keep the host lean and clean it would give you full control over the state of the various apps.

I do something similar with VMWare on some of my machines and, in particular, a Windows box - running up specialist VMs to avoid clashes and over-installing on the host, except where the native hardware must be accessed directly.

It causes a slight hit in performance but nothing I can't live with for the benefit of being able to hibernate stuff on my laptop too.

---

