---
title: "Trouble connecting front eSATA"
date: 2008-04-28
forum: Hardware
---

### Post by twin_57103 on 2008-04-28
Hi folks,

This is more a hardware question than an Ubuntu question, but I hope you'll bear with me.

I recently got an enclosure to convert a SATA hard drive to external.  I've got both USB and eSATA connectivity on the enclosure.  USB works fine, but I'm having trouble with one of two eSATA connections.

This is a custom-built computer; all of the internal drives are SATA (see sig).  I've got 2 eSATA connectors: the rear panel with an eSATA port built directly on the motherboard, and on the front panel, connected to the internal SATA connectors.

I got the rear panel connection to work after a little fiddling, but I've had no luck with the front panel.  The rear panel behaves like any removable media (although I had to grant access to mount it in Ubuntu the first time), mounting automatically.

  Although there's no master-slave relationship with SATA, I have noticed that the order of the drives does matter (I can only boot from DVD drive that is first in the sequence).  

SATA 0: primary hard drive, 320 Gb total, 160 Gb each to Windows (NTFS) and Ubuntu (ext3).
SATA 1: second hard drive, 320 Gb NTFS (single partition)
SATA 3 & 4: DVD drives
SATA 5: front eSATA
SATA 6: unused

I also tried moving the DVDs to SATA 4&5 and putting the eSATA in SATA 3 in case that made a difference.

I'm not sure why the front interface isn't working - brackets like this are pretty common to add eSATA to computer that don't already include it (the enclosure came with one of them).  Any thoughts/advice?

Thanks for your time!

---

