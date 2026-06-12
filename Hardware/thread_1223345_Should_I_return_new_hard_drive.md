---
title: "Should I return new hard drive?"
date: 2009-07-26
forum: Hardware
---

### Post by hansamurai on 2009-07-26
Just built a new computer this weekend, and encountered a series of problems while trying to install Ubuntu 9.04 that seem to be related to the hard drive.

Here are some of the symptoms I saw (not all indicated HDD problems however):
[LIST]
[*]After selecting Install Ubuntu the loading screen would go by but then a black screen would appear with just a blinking cursor.
[*]Similar as above but it would at least display the wallpaper and then just sit there.
[*]Got past all the installation instructions and then it froze on the partition/formatting phase.
[*]At this point I decided to try and install Vista (only other install disc I had laying around) and that blue screened during the first phase, installation file expansion I believe.
[*]Tried installing Ubuntu again after successfully getting into the live CD and wiped the partitions there.  After all the installation options, Ubuntu complained that either the disc was bad (burned too fast, bad reader) or that the HDD was bad and bombed that install.
[/LIST]

After this is all said and done, I was finally able to successfully install Ubuntu 9.04 Desktop 64-bit (with the same disc that might have been bad).  I'm using it now with seemingly no problems.  I did a short SMART test that reported no issues, I'm running the long one now.

The hard drive is a 640GB Western Digital Black bought from Newegg so I'm not anticipating any problems exchanging it, just wondering if I need to go to the trouble.

There's a few more things I can do on my own end like trying out one of my other drives to make sure it is the HDD and not the RAM or something else.  And the long SMART test will be done in the morning.  I'm going to give Vista another shot tomorrow too to see if it was all just a fluke.

Any advice would be great, thanks in advance for all the help.

---

### Post by Ravernomina on 2009-07-26
one dnt feel bad i need to return my Mac because im getting horrible disk performance on Mac OS X.


Try another HDD see what come out... Also check to see if ur RAM is in all the way and also try the RAM dance (RAM swapping) try even switch ports on your mobo and see if that helps.. ( SATA Port 0, IDE Master)

---

### Post by hansamurai on 2009-07-26
Thanks! I wish I had more SATA drives to try out but my last computer was so old (Athlon XP 1800+) that I only have a bunch of PATAs and then one 1TB SATA for backup and media.

The long test did pass though.  Is there anything like Memtest86+ that I can run but for hard drives?  Or is SMART just about it?

---

### Post by hansamurai on 2009-07-26
I don't think that it was ever a hard drive issue, but instead the memory.  My memory is DDR2-800 that is sold as 1066, so I just assumed I could clock it up to 1066 immediately without touching the voltage, etc.  Turns out, there's a bit of tweaking to do.

Memtest was failing when clocked to 1066, but was fine at 800.  I'll reply again if I notice anything else.

---

