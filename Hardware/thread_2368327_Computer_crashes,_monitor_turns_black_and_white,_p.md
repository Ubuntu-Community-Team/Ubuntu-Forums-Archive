---
title: "Computer crashes, monitor turns black and white, pages don't &quot;respond&quot;."
date: 2017-08-09
forum: Hardware
---

### Post by gmolivier on 2017-08-09
Ubuntu 16.04.  I use Chrome, Firefox and Chromium browsers.  They all give same problem.
This problem happens periodically.  It will occur when i am just reading news sites, both local and national.
This also happens when i am watching UTube videos, especially when i have tabs open, each with a UTube video on pause.
This is a now-and-then problem, but several times a week.  It is not a new problem; i have written here about it maybe a year ago, no replies that i know of.
Could this be related to ram, hard drive, cpu,....?

thanks,
gmolivier

---

### Post by efflandt on 2017-08-09
An application will "gray out" when it is waiting for something behind the scenes and will be unresponsive (no focus) at that time. I have not seen that in a very long time.

How much RAM do you have and how much is actually being used at the time (free -h)? If using all of it, swapping memory between RAM and disk (swap) can result in lag. Not sure if a network interruption could cause that. It can also happen with a slow CPU or possibly failing hard drive having read/write issues. Check **dmesg** when that happens and see if that reveals anything.

I have enough RAM (was 8 GB, now 16 GB) and am running from SSD, so I do not even have a swap partition. And I am even using RAM for /tmp (tmpfs). I don't actually use all that RAM for programs, a vast majority is used for automatic disk cache.

---

### Post by ajgreeny on 2017-08-09
If you are seeing large blocks of black and white it is possibly related to enabling hardware acceleration in the preferences for the browsers, and is perhaps related to your hardware's abilities not being up to the required level, or using the incorrect driver for your graphics card.

Try disabling hardware acceleration in the browsers to see if that helps.  If the problem occurs in other applications than browsers it may be something else causing the problem.

---

