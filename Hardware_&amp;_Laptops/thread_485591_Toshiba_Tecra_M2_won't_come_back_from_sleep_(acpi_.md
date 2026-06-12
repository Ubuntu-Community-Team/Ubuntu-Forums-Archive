---
title: "Toshiba Tecra M2 won't come back from sleep (acpi related?)"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by fuzzycuffs on 2007-06-27
So I've got a Tecra M2, Ubuntu 7.02.  Working great.

But the thing that doesn't seem to work is coming back from sleep.  It'll go to sleep fine if I leave it idle or close the lid, but when I re-open the lid to wake it up from sleep, the power LED on the front comes on, the HDD indicator sometimes blinks, but the screen doesn't come back up.  Going to any of the terminal windows won't work, trying to forcequit X with control+alt+backspace won't work, etc.  I end up having to force shutdown by holding down the power button.

Any ideas?  Google is no help except for an interesting toshset utility that also seems to be called in /etc/acpi/resume.d scripts.

Maybe ACPI isn't turned on or the modules haven't been loaded?  It's really been a while since I used linux heavily, back when I did I was compiling kernels in slackware so the newfangled behind the scenes approach of Ubuntu is a bit refreshing but I also don't know what's going on.

Thanks for any info!

---

### Post by LazyTownRocks on 2007-07-02
I had the same problem on my Tecra-M2 and resolved with a full re-install (Dapper-Drake 6.06 and all updates including MediBuntu), it now wakes up Ok and only causes a problem when I tell it to sleep - then the only way I can wake it back up is to hold down the power and do a full restart.

---

