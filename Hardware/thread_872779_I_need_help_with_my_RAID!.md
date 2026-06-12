---
title: "I need help with my RAID!"
date: 2008-07-28
forum: Hardware
---

### Post by ericduffy on 2008-07-28
Hi folks,

I'm putting together a RAID 10 on Hardy.  I've got 8 Terabytes running on a 3Ware 9500S series controller (with the RAID-10 that should be ~4TB usable).  The controller BIOS recognises the disks and tells me that there is 3.63TB available (as it should be) so there's no problem with them.

My issue is getting Ubuntu to recognise all 4TB.  I just doesn't partition to the entire 4 no matter what I try -- and I do want all 4 on a single partition.  This is going to get used as a data repository and for the sake of future convenience I want it all contiguous.  I'ved walked through a number of how-to pages.  My understanding is that ext2 and 3 should have no problem handling 4TB.

Gparted won't let me have a partition of more than 1.81TB though, and that's with some coaxing.

Any suggestions? :)

Eric

---

