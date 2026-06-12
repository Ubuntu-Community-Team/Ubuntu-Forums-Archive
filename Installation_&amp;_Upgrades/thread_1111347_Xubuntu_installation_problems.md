---
title: "Xubuntu installation problems"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by louis058 on 2009-03-30
I downloaded intrepid ibex iso, then burned the iso image onto a CD-R, and I try it while using windows, it works, it shows the demo and install stuff, then I restart the computer, go to Setup, and change the 1st boot device to CD-ROM, and the 2nd to IDE-0 (which is the hard-drive), and save and restart, it still boots into windows, so then I stop it from booting into anything other than CD-ROM, and it says "cannot find boot item in CD-ROM" or something along those lines, the point is, it wouldn't load the Xubuntu installation screen, so then I try all the other boot devices EXCEPT for CD-ROM and hard-drive, INCLUDING floppy, and it still won't load... What's going on?

---

### Post by louis058 on 2009-03-31
oh yeah, and the computer's running windows XP, if that helps

---

### Post by dandnsmith on 2009-03-31
The PC isn't seeing the CD as bootable.
You, by your own account, didn't fall into the trap of burning the iso to the CD, so that all you see on the CD is the iso file - so there's something else wrong.

First - did you do the checksum test on the iso file after downloading it (the obvious one is MD2SUM, and you can get a handy little checker to run under XP)?

2nd - have you tried any other bootable CDs, just to see if any can be booted.

---

### Post by louis058 on 2009-03-31
> **dandnsmith said:**
> The PC isn't seeing the CD as bootable.
You, by your own account, didn't fall into the trap of burning the iso to the CD, so that all you see on the CD is the iso file - so there's something else wrong.

First - did you do the checksum test on the iso file after downloading it (the obvious one is MD2SUM, and you can get a handy little checker to run under XP)?

2nd - have you tried any other bootable CDs, just to see if any can be booted.

no, i haven't tried either of those, i'll try them now ;)

---

### Post by louis058 on 2009-04-01
oh my god, i am so stupid!

i checked the md5sum of the iso, it was correct, then i downloaded the Ultimate Boot CD iso, to burn onto a cd, to check whether the computer could actually boot CDs, when I saw that the CD-R that I was using said 52x... i then wondered, whether the computer's optical drive was a 52x CD drive... i went to check, and saw that it was a 42x10x20 CD drive, or something along those lines, then i saw that RIGHT UNDER THIS DRIVE THAT I HAD USED, was a 52x CD DRIVE!!!!!!!!!!!! so i had put in a 52x CD into a drive that couldn't use it (old computer), so then i put the xubuntu CD into the proper 52x CD drive, and EVERYTHING went well, meaning I just wasted a few hours of my life trying to figure out what the problem was...

i'm just so used to just one optical drive on my main computer :D

---

### Post by dandnsmith on 2009-04-03
Glad to hear you've got it sorted.
It's a rare person who never slips up on a problem in this class.

---

