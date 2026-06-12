---
title: "Raid Array HDs disconnecting"
date: 2008-12-29
forum: Hardware
---

### Post by slick666 on 2008-12-29
I'm having some hardware problems with a Server RAID array and I don't see a good solution. I'm hoping someone will have a suggestion.

Here is the hardware run down
Raid Card: 3Ware 9650SE-8LPML
Hard Drives: Seagate 7200.11 500GB Drives x8
Case: Lian Li V2000B

The problem as far as I can see is that either the power of sata cables seem to be loose. The server is sitting in a closet where I control who goes in and out. I know for a fact that no one has been in or around the machine yet still I get HDs that are degraded. The I can't seem to figure out why the HDs are undetectable. They can be out for a short time and come back without having to do anything or I can go in open up the case and jiggle cables until the come back. The Raid card automatically starts rebuilding the raid server one the hd is back on for 2-3 seconds so the rebuilding might be happening more often than I think.

My plan at this point to to first create a custom power cable that connects all the Hds and test it to be sure there are no weak links.

The sata cables are a problem because the raid card has two multi-lane connectors so I'm using the the "squid" that came with the card to connect all the hds. If anyone has some suggestions I would like to use "left-handed" sata connectors that Clip into the hds but I would then have to convert those into a multi-lane cable to connect to the raid card.

Any help would be appreciated.
Thanks

---

### Post by AndyInNYC on 2009-01-28
My array was dropping a drive (same drive every time regardless of which port it was on).  I have the 3ware 9500S.

I pulled the drive and ran the Hitachi diagnostics and turned ON the SMART setting - it was a brand new drive and the only one with this issue.

The drive is now in the array and quite happy (I hope).

Hope this helps.

Andrew

---

