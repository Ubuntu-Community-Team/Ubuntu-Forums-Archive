---
title: "RAID array not working after upgrade?"
date: 2011-10-18
forum: Hardware
---

### Post by Eemerica2s on 2011-10-18
Not sure which problem this is exactly... I have a Raid 1 setup of 1TB for each drive. After the upgrade to 11.10, it stopped working and was listed as "DEGRADED." No issue, I removed a drive and resynced it. The weirdest thing about the whole situation was what I was being told in the Volumes on Disk Utility.

Free 112GB
Unknown 871GB
Unknown 372GB
Free 257GB
Free 18446743TB (I kid you not)

So after it resynced, still nothing. State changed to Running, so I hit "check array" and it's repairing as we speak. Here's where my question comes in...

Should I cancel that and just reinstall the 11.10 update? I got a bunch of errors and something about ushare failing to upgrade/install and I kept getting a bunch of errors using mdadm in terminal. Or, will my array be okay after this repair and I should let it continue (it's probably going to take a good 17 hours to repair...)?

---

### Post by Eemerica2s on 2011-10-20
Okay let's try this again.

I just reinstalled everything and went back to 11.04 which gave me much less problems.

How do I go about *finding* the array now?? Hard drive light is on, but Disk Utility is telling me nothing...

---

