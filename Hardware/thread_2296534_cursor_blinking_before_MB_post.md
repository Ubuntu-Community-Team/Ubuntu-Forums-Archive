---
title: "cursor blinking before MB post"
date: 2015-09-26
forum: Hardware
---

### Post by mattdawolf on 2015-09-26
I have a 
**[GA-X79-UP4]("http://www.gigabyte.com/products/product-page.aspx?pid=4288")**

installed on a system that I use as a NAS. It has recently started to do some odd behavior on powerup. Before it reaches its POST screen it just blinks a cursor.

I do not understand what is going on. Any advice? Had to dropbox the 6 MB video.

[https://www.dropbox.com/s/7pzi40a9ygjdhid/20150926_110558.mp4?dl=0](https://www.dropbox.com/s/7pzi40a9ygjdhid/20150926_110558.mp4?dl=0)

---

### Post by Dreamer Fithp Apprentice on 2015-09-26
Does it eventually boot or does it just hang there indefinitely? Can you get to the bios setup? If so, in some bios setups there is an option for a more thorough or a shorter POST. You might try the more thorough one. Is it possible you have it set to skip POST and the blinking cursor is taking place when it is trying to boot from some media? If it takes a long time but does eventually boot, I'd wonder about 2 things - could the boot device be unusually slow (which might be a warning sign that it is going to fail soon) or could it be trying to boot from something else first (like maybe a cd you left in a cd drive for instance) and looks there before going on to the proper media.

If the answers to those questions are in the video, sorry. I don't even have a player installed ATM.

---

### Post by mattdawolf on 2015-09-26
It's been suggested to me to try a bios upgrade. It doesn't matter which of the two SSDs is listed as the hard drive to boot from. It does eventually boot, but this is completely abnormal for it to do. It should just flash the post screen then get to booting a HD.

---

### Post by weatherman2 on 2015-09-26
I don't see how a BIOS upgrade will solve anything, if this behavior didn't occur before.  BIOSes do not "go bad."  A BIOS upgrade might fix some existing issue or a compatibility problem with a new CPU or RAM or something.  In your case, I wouldn't bother.

Try this: unplug all of your drives and USB devices temporarily, then power up and see if the behavior changes at all.  If so, by process of elimination, plug one in at a time and see which one is the likely culprit.

---

### Post by Dreamer Fithp Apprentice on 2015-10-01
concur ^.
Also, possibly I left this question too implicit:
Have you checked the boot order in the bios setup? Is it possible it is taking a while to attempt to boot something unbootable before moving on to the preferred device? Like for instance, an audio CD, a thumb drive, and old internal hd? If the device itself is just getting slower, I'd consider it at risk of imminent failure and backup accordingly.

---

### Post by mattdawolf on 2015-10-01
I have not troubleshot this further, but it seems to be behaving after a boot order change. 

> **Dreamer Fithp Apprentice said:**
> concur ^.
Also, possibly I left this question too implicit:
Have you checked the boot order in the bios setup? Is it possible it is taking a while to attempt to boot something unbootable before moving on to the preferred device? Like for instance, an audio CD, a thumb drive, and old internal hd? If the device itself is just getting slower, I'd consider it at risk of imminent failure and backup accordingly.

---

### Post by Dreamer Fithp Apprentice on 2015-10-01
Glad you got it working. You probably either had some non-bootable (or inconsistently bootable - I see this with CDs a lot) media in a place set to boot first or possibly a removable media DRIVE that was taking a long time to tell the OS that it was empty. If it still seems to be working ok now, it would be good to mark your thread "solved".

---

