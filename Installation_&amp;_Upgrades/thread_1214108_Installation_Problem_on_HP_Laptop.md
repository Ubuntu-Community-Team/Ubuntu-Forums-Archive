---
title: "Installation Problem on HP Laptop"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by ASCIIraider on 2009-07-15
Hi Guys,

Well after a successful 7.04 install I wanted to get a newer supported version of Ubuntu.  However neither 9.04 nor 8.04 will install.  I am a total Linux noob so am rather perplexed by this turn of events.  Some searching has so far yielded no results save that I found a post from someone with an LG laptop who was experiencing the same problem.

Lappy is an HP nc8000 P4-M/1.4 with 512MB RAM, 160GB HDD, 32MB ATI video.  There was some mention about Ubuntu not liking some Intel chipsets (845 I think).  The error always comes in at around 44% and says something along the lines of input/output error - usually caused by a bad disk, but I am using quality blanks and burning at 8x.  I think the error number was 5.

Has anyone got any ideas as to how I can install either Ubuntu 8 or 9 on my laptop?

Thank you. :)

---

### Post by mynameinc on 2009-07-15
> **ASCIIraider said:**
> Hi Guys,

Well after a successful 7.04 install I wanted to get a newer supported version of Ubuntu.  However neither 9.04 nor 8.04 will install.  I am a total Linux noob so am rather perplexed by this turn of events.  Some searching has so far yielded no results save that I found a post from someone with an LG laptop who was experiencing the same problem.

Lappy is an HP nc8000 P4-M/1.4 with 512MB RAM, 160GB HDD, 32MB ATI video.  There was some mention about Ubuntu not liking some Intel chipsets (845 I think).  The error always comes in at around 44% and says something along the lines of input/output error - usually caused by a bad disk, but I am using quality blanks and burning at 8x.  I think the error number was 5.

Has anyone got any ideas as to how I can install either Ubuntu 8 or 9 on my laptop?

Thank you. :)

Did you MD5 the image before burning the disk?  Also, before installing, use the "Check the CD for defects" option.

---

### Post by Mark Phelps on 2009-07-15
Based on Googling, looks like your lappy uses a Radeon Mobility X700 -- which is not supported with restricted drivers in Ubuntu 9.04.  So, if you want to use accelerated hardware drivers for it, you can't upgrade beyond 8.10; otherwise, you'll be forced to use the open source drivers.

---

### Post by ASCIIraider on 2009-07-15
Hi,

No I didn't do the MD5 check, how exactly do you do that?

I assume the "check disk for errors" option is on the first menu?

I am currently running 9.04 as a live session user with no problems, does this mean anything?

Thanks for your help.

---

### Post by ASCIIraider on 2009-07-16
Hi,

There are lots of different nc8000 models, I think X700 sounds a bit too advanced for my lappy as it's a very early model.  Actually it might only be a 16MB model, I think Rage128 rings a bell.

I find it hard to believe that it would work with 7.04 but not 8.04 or 9.04.

Any more suggestions?

Cheers.

---

### Post by mynameinc on 2009-07-16
> **ASCIIraider said:**
> Hi,

No I didn't do the MD5 check, how exactly do you do that?

I assume the "check disk for errors" option is on the first menu?

I am currently running 9.04 as a live session user with no problems, does this mean anything?

Thanks for your help.
That is... peculiar... anyhow, here's your links:
MD5ing:[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Checking CD for defects:No link neccesary, it should be on the same menu as 'Try without any changes to system', 'Install', etc.
Hope I helped.

---

### Post by Mark Phelps on 2009-07-16
> **ASCIIraider said:**
> Hi,

There are lots of different nc8000 models, I think X700 sounds a bit too advanced for my lappy as it's a very early model.  Actually it might only be a 16MB model, I think Rage128 rings a bell.

I find it hard to believe that it would work with 7.04 but not 8.04 or 9.04.

Any more suggestions?

Cheers.
Well, I didn't have the exact specs, so went on the closest I could find with Google.

You shouldn't have any problems with 8.04, but 9.04 won't support the older ATI cards/chipsets with accelerated drivers, and there are problems in 9.04 with some Intel chipsets as well.

The drivers are different with each release because the kernels are different (among other reasons), so just because a card/chipset worked with an earlier release is no guarantee that it will continue to work with a later release.  There have been LOTS of posts in the forum from folks who upgraded from 8.10 to 9.04 and suddenly lost video.

---

### Post by ASCIIraider on 2009-07-17
Ok so what's going on here?

I downloaded 8.04.3 and it's MD5 checksum again does not match!  I also burnt it to CD to run the check disk and again it comes back with 1 file corrupted!

What the?

Is there something I am missing here?  I have used Firefox, Chrome and now Orbit Downloader to get these files but out of four downloads, three have been corrupt.  

Does anyone else have these problems or am I just unlucky?

---

### Post by ASCIIraider on 2009-07-20
Just downloaded 8.04.3 again and the MD5 hash still does not match according to WinMD5sum.  I'm about to give up on Ubuntu I think...shame :(

---

