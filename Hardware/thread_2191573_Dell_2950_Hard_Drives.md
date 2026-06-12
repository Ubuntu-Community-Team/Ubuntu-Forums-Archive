---
title: "Dell 2950 Hard Drives"
date: 2013-12-03
forum: Hardware
---

### Post by racrbilly67 on 2013-12-03
I am looking at purchasing a Dell 2950 server to use for a NAS or really any other type of server for my home use. I have run into the problem with a dell hard drive enclosure at work where it would only accept Dell certified drives into the array. Does anybody here know if that would be the same case for the server? I am guessing since it is a Dell (PERC) Raid controller that it would be.

Thanks.

---

### Post by tgalati4 on 2013-12-03
I found a bunch of used server drives on craigslist for $6 each to serve as back up for my Dell PowerEdge 1750.  You just need to make sure that the drives will work with the PERC RAID controller.  Dell's website provides a list of drives that are "certified" to work with this hardware.  In reality, you can stick any kind of SCSI drive that will fit, but to get the hotswap to work and to get the RAID BIOS to recognize the drive, you need to stick to the narrow list of supported drives.

The bigger issue with these Dell servers is the power consumption (200 to 240 watts) when running 24/7 and the noise (think jet engine) when used has a home NAS.

If you want to use newer drives, find a SATA card that will fit the server chassis and find a way to stuff some new SATA drives into the empty spaces.

---

