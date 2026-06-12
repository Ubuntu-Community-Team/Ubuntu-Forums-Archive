---
title: "Trouble Installing Newest Ubuntu"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by pklotus7 on 2009-10-23
I was given a 2yr old dell that ran windows xp. The previous owner had issues probably with viruses that screw up the computer. I tried to re-install windows without success (keep freezing up) so I decided to try Ubuntu. 
 
When I try and install Ubuntu I eventually get a screen that looks like this:
 
[ 2.441271] BUG: unable to handle kernel NULL pointer dereference at 0000009...
[ 2.441435] IP:<1>BUG: unable to handle kernel paging request at b94fd641
[ 2.441646] IP: 
 
Then it stops here and does nothing. I am unsure of what I need to do to fix this issue and continue with the install.
 
Hopefully I can find some help.
Thanks

---

### Post by earthpigg on 2009-10-23
since Windows and Linux are ***both*** having problems, it kind of sounds like a hardware problem.

test for faulty RAM: [http://www.memtest86.com/](http://www.memtest86.com/) <-- will need to burn a memtest LiveCD

test for faulty hard drive: [http://en.wikipedia.org/wiki/Badblocks](http://en.wikipedia.org/wiki/Badblocks) <-- from the ubuntu live cd you already have

$0.00 solutions:

if it's faulty ram: open the box up - if there are two sticks of RAM then hopefully only one is bad. take one out, then run the test. then take the other out and run the test again.

if its a faulty hard drive: Linux does not need a hard drive -- an external USB thumb drive sitting in your desk drawer can be put to use as a "hard drive".

---

### Post by pklotus7 on 2009-10-23
Thank you for the help.
Here is the deal.  Memory checked out ok.  I tried a different hard drive (4 to be exact).  With one of the hard drives I was able to get to the 2nd step of the install BUT the install stop and the computer froze.  When I tried it again all hard drives gave me the same error message I stated earlier in my OP.  I even tried it with the USB drive and got the same result.  
 
Could there be something wrong with the motherboard?  I know this problem is starting to get away from ubuntu problems and more to computer problems but I am hoping that I can still find a way to install ubuntu on this computer.
 
Any suggestions besides trashing the computer (which I am about to)
 
Thanks

---

### Post by kylegio on 2009-10-24
i had something KINDA similar to this happening, however it was intermittent and i kept thinking i had viruses or that i was messing something up, turned out that the disk controller on my motherboard was screwy, RMA'd it and never had the problem again. but to me your problem sounds more like a ram issue, have you tried running a live-cd or a usb boot? with no hard drive in the computer at all?

---

### Post by urugTON on 2009-10-24
I admire your patience.  Mine would be gone.

Have you checked the CD?  There's a test that can be done right at the start as I remember.

Good luck.

---

