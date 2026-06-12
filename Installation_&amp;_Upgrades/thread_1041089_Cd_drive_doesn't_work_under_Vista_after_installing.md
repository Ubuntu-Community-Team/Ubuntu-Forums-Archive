---
title: "Cd drive doesn't work under Vista after installing 8.10"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by wibbleypants on 2009-01-16
Just installed 8.10 on a friend's Acer Aspire 5613. After the install, when he boots into Vista, the CD drive no longer functions. Vista says it can't load the driver. Remove the drive in control panel and do "find new hardware" and after finding the drive, it still can't load the driver. Boot into ubuntu and the drive works fine.

The only change I made was to change the boot order to boot from the install cd. Can't see how this can have duffed anything up.

Any ideas anyone?

---

### Post by Tim Sharitt on 2009-01-16
Try changing the drive order back to original. Swaping it may have changed the way Vista sees the drive. It's not really a fix, but if that's the case, it may help to find a solution.

---

### Post by wibbleypants on 2009-01-18
Tried changing the boot order back, but no joy.

---

### Post by Craigy90 on 2009-01-18
I had an optical drive stop working in Vista a little while ago, (although I had not installed Ubuntu on that computer), and stumbled upon a solution.

Make sure your situation matches before you try this:

> **Situation**
There is a yellow exclamation mark for CD/DVD drives in Device Manager. The device status in the properties of the driver might indicate an error code, for example 32, 37, or 39. Or the drive simply does not appear in My Computer or Device Manager.

Here is the the main thread, and a program to do it for you:

[http://forums.driverguide.com/showthread.php?t=30011](http://forums.driverguide.com/showthread.php?t=30011)

And here is the manual solution:

[http://forums.driverguide.com/showthread.php?t=21669&page=4](http://forums.driverguide.com/showthread.php?t=21669&page=4)

Hope this helps. It seemed like a long shot to me, but now I have my drive back! :)

---

### Post by wibbleypants on 2009-01-18
Thanks for that. I'll give the geezer that url tonight. Shame I can't get the page to display in spanish though. I can translate myself, but if it goes tits-up, I'd rather he'd read any disclaimer first ie; I'd rather he went in with eyes open.

I'll let you know how we get on.

---

### Post by wibbleypants on 2009-01-19
Ok. The program didn't work, so followed the instructions for deleting the registry keys. This worked fine.

Thanks.

---

