---
title: "Kernel Panic"
date: 2008-10-14
forum: General Help
---

### Post by kakemann on 2008-10-14
I have been having some problems with kernel panic, but I cant seem to pinpoint the problem causing it. Today I managed to take a photo of the error message.

The computer has been running smoothly for a few days now, but today it "went down". I was not able to use SSH, it did not respond to ping, and I was'nt able to see anything locally on my screen either. I turned it off the hard way, and when I booted it back up I got this error. 



Does anyone know what the problem is? 

Is there any way I can see the error before the computer went down? In some kind of log or something, I have been looking but no luck....

I have run the memtest, and it reported no errors.

regards
Chris

---

### Post by phidia on 2008-10-14
Logfiles are in /var/log. Since this is a kernel panic it would make sense to check kern.log but that can be laborious work.(there's a lot of output in the logfiles)

I would check physical connectors and bios settings too.

If none of the above helps or shows anything you can boot from a live cd and try and mount your partition(s).

---

### Post by kakemann on 2008-10-16
I was able to boot the computer after a while, and it has now been running for a while. 

I have been checking the log files, and kern.log especially, but I can't find any errormessages from just before it shuts down.

Is there any way I can turn on more logging i kern.log to see if I can get anything from that?

---

