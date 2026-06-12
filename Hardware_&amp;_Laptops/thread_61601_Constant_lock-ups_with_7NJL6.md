---
title: "Constant lock-ups with 7NJL6"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by bradg on 2005-09-01
I'm putting together a new PC for Ubuntu and I am getting lockups during installation (Either a hard lock during the formatting of the hard drive or a segfault during base install).  I've tried with Warty, Hoary, and Breezy Colony 3.  My motherboard is an nForce2-based Chaintech 7NJL6.  Nothing seems to be overheating.
An interesting thing to note is that running a LiveCD, both the warty live CD and SLAX, works very well and there are no lockups.  memtest passed perfectly on SLAX.  And when I tried to format hda1 while in the Ubuntu LiveCD, I got a lockup again.  
So it is apparently something related to the hard drive or the I/O controller.  I believe it is the I/O controller because the hard drive was working just last week in an older system and this morning I ran out to buy a new hard drive just to make sure that wasn't the problem.  Same symptoms with the new drive?
Is there some special boot parameter I have to use with my motherboard or something?  How do I even figure out what I/O controller is onboard?  Please help.  This is quite frustrating.  Thank you.

---

