---
title: "raid 1 hdd boots individually but hangs when both are connected"
date: 2016-01-02
forum: Hardware
---

### Post by jeffrey_purcell on 2016-01-02
if posted somewhere else forgive me.  i have currently a raid 1 configuratiion with 2 identical hdd. everything was working perfectly until one day system would not boot.  checked drives and i can boot each drive seperately with no issues. all files are intact with no apparent issues on either drive. when both drives are installed. system hangs and will not finish booting. i am currently running 14.04 lts server, with plex media installed. any suggestions with this would be very helpful

---

### Post by weatherman2 on 2016-01-02
What kind of RAID?  Software or hardware?  (If you used mdadm in Ubuntu to setup the RAID, then it's a software RAID.)

Do you get any messages when it hangs?

Have you checked the S.M.A.R.T. health of both drives to make sure there aren't any flagged issues?

---

### Post by jeffrey_purcell on 2016-01-02
sorry for lack of info. it is software raid.  actually figured it out. one of my drives was actually bad even though the tests run showed it as good.  both drives are identical so took both out of system and put in enclosure and ran tests from another system. one of the drives is fully functional with no errors or problems. the other has bad sectors that got reallocated. i have since removed the drive and will replace in the next day and rebuild the array. just weird that when i ran smart both drives passed. just thankful i had another system and enclosure to use. off note when i reinstalled grub i was able to get the system to boot even though one of the drives was bad.  thanks for your help i forgot about smart and that is what prompted me to run from different system.

---

### Post by weatherman2 on 2016-01-02
Well...S.M.A.R.T. is S.M.A.R.T. - it's built into the drive itself.  Unless there's something in your original system where the control can't communicate with the S.M.A.R.T. controller inside the drive or something (or disabled?), you should get the same S.M.A.R.T. information no matter what system you use to read it.  I monitor S.M.A.R.T. all the time on my servers - not always providing an early warning of a drive problem but often does.  I'd take the opportunity while you still have the bad drive to make sure you can see the real S.M.A.R.T. issues with it now so you would see them in the future without needing to remove the drives and test them.

---

