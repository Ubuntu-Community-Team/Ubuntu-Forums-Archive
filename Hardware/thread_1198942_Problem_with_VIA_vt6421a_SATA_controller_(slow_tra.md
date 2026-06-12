---
title: "Problem with VIA vt6421a SATA controller (slow transferspeeds)"
date: 2009-06-28
forum: Hardware
---

### Post by T.lancer on 2009-06-28
Hi I just upgraded my Homeserver with 2 1TB Western Digital Drives.  I needed to install a new SATA conroller.  As I had a VIA vt6421a PCI controller around, I installed it.  All seemed to work, I was able to format the drives with ext3 and copy files over to it.  However I now discovered that the transfer speeds aren't what they should be.  The strange thing is, I can wirte with around 20 MB/s over the LAN when copying to the drives. But when reading, I only get about 1 to 1.5 MB/s.  I've tested this on many PCs in the network, all with the same speeds.  When reading or wirting from any of the older 500GB drives I get normal speeds. So it must be something with the controller.  I have allready set the drives to SATA 1.5 Gbps, but that didn't do anything.

Now, I know I know... I'm still running with ubuntu 7.10 and I really need to upgrade.  But I want to know if there is something that I can test before trying to reinstall with an LTS.

I'm going to be installing an other 3x 1TB drives soon with one raid 1 so I'd rather reinstall then.  The older 500GB drives would then be removed.

thanks for any help

---

### Post by T.lancer on 2009-06-29
has no one got any idea?

---

### Post by cllemke on 2009-12-29
I know this is an older post, but did a search for the SATA controller and have the same exact problem. Went from a 300GB Seagate to a 1TB WD Caviar Green. 300GB drive worked fine, but the 1TB writes at 20MB/s but reads at around 1MB/s in Windows XP Pro SP3 x86. Were you able to remedy this? If so, what did you do?

Thanks
-Chad

---

### Post by T.lancer on 2009-12-30
unfortunally no.

I ended up buying a server grade PCIx SATA RAID controller for about 40€.  fixed the problem instantly.

Now I'm running a RAID 1 setup with 2 1TB drives for the main system and backups.

---

### Post by cllemke on 2009-12-30
That is what I figured would need to be done. I don't think this controller likes the 1TB drives. Oh well. Reason to go to Fry's and look around at what else I "need". =) Thanks for the response.

---

