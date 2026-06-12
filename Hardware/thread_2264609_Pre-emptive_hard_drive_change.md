---
title: "Pre-emptive hard drive change"
date: 2015-02-08
forum: Hardware
---

### Post by vanhenryjr on 2015-02-08
My hard drive is beginning the "whine of death". I do back up my hard drive via an external one. 

How do I restore or replace this hard-drive. Do local dealers do this? Using 14.04 on a system76 gazelle pro

---

### Post by weatherman2 on 2015-02-08
Use S.M.A.R.T. to monitor the health of your hard drive.  Try GSmartControl and look at the Attributes, to see if any Attribute has already flagged in red or pink.

It is fairly easy in most cases to replace a hard drive if you are so inclined.  "Cloning" means copy the contents of the old drive to the new one, exactly, so you just swap drivers afterward and you're finished, nothing to re-install.

Clonezilla is not that user friendly but works pretty well.  There are other free cloning tools out there that may be easier to use.  Acronis True Image offers free versions of its imaging/cloning software to users of WD and Seagate hard drives (but they are branded by the HDD manufacturer).  They may work only in Windows, or you may be able to create boot/rescue discs (or USB boots) from them.

You can directly clone an old hard drive to a new one if you can attach both drives to the same computer at the same time.  It's not simple to clone a larger hard drive to a smaller one, but cloning a same-size or smaller drive to a larger one is pretty easy, Clonezilla and the other software can handle that automatically.

If you can't connect both drives at the same time, you can do it in two steps with Clonezilla: first save an image of the old drive to your external drive (takes a lot of space but is stored in files on the drive, not using the whole external drive).  Then swap the new drive in, boot up Clonezilla, and restore the image you just made to the new drive.  Takes longer that way but does not require any USB HD adapter for say a laptop.

Lots of demo videos - look on YouTube.  Search for "clonezilla" for example.

---

