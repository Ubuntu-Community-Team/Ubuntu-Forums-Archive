---
title: "Repair HDD that Will Not Format?"
date: 2015-01-04
forum: Hardware
---

### Post by Dave_Claxton on 2015-01-04
Hi Guys,

I recently upgraded the HDD in my laptop and wanted to use the old one as a back up/storage drive. The drive is a Samsung HM500JI and worked fine as the main drive in my laptop. After removing it i gave it a quick format, which went ok, then tried to copy all my music files onto it to keep as a secondary back up. The file transfer failed about 2/3rds of the way through (approx 200gb total). Ok, no probs...s**t happens! Then i tried to do a full format.....no joy......5 or 6 attempts later, still no joy. 

Is this drive bricked or can it be salvaged?

I've tried to do a full format using :

1, Ubuntu (Disk Utility)
2, Ubuntu (GParted)
3, Active Kill Disk
4, Windows 7

all with similar results.....the format gets approx 40% complete then fails.

Any other ideas? or anyone had a similar experience with successful results?

Thanks in advance guys.

---

### Post by weatherman2 on 2015-01-04
Install GSmartControl in Ubuntu, then check the drive's S.M.A.R.T. Attributes.  Look for any Attributes highlighted in pink or red on the old drive.  (For example, a raw value greater than 0 for number of Pending Sectors.)  It's always possible the drive was/is failing.  Hard drives fail all the time.

If there are pending sectors (sectors that couldn't be read by the drive's firmware), you could try zeroing out the whole drive and see if that clears them.

---

### Post by Dave_Claxton on 2015-01-04
Thanks for that Weatherman2, have installed GSmart and ran a test, here are the results...............this info is beyond my tech knowledge so all help appreciated :-)

---

### Post by weatherman2 on 2015-01-04
OK, I see it.  Time to put that drive to rest - it has 2,668 bad sectors ("Current Pending Sector Count").  Sometimes if you have only a few bad sectors, you clear them out by zeroing the drive, but I've never seen a few thousand or even a few hundred clear.  The surface is probably failing.

There are tools that will zero out a drive if you still want to try (I'm guessing almost zero chance it will work in this case - but not much to lose I guess).  I usually use DBan or Parted Magic boot disks to zero out a drive - but a quick way to initiate it (but time consuming - figure hours) would be to run this command from a terminal in Ubuntu:

```
sudo dd if=/dev/zero of=/dev/sdb bs=2048
```

and come back in a few hours (the command prompt will finally come back when it is complete - there is no status output).  After it's done, check S.M.A.R.T. Attributes again.  If magically the number of pending sectors has returned to 0, then you were very lucky - but I doubt it.

Be *very *careful with the dd command! I am assuming /dev/sdb is your old drive and not the new one.  Mistype it and you could zero out the wrong drive.  The dd command is powerful but dangerous.

---

### Post by Dave_Claxton on 2015-01-04
Thanks weatherman2, have used Parted Magic before so i'm having one last attempt with that, i'll leave that running overnight, if it fails i'll abandon it and get a new drive. Thanks for the help.

---

