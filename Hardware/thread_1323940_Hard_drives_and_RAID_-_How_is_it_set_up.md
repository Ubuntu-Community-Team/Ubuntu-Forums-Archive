---
title: "Hard drives and RAID - How is it set up?"
date: 2009-11-12
forum: Hardware
---

### Post by ed-koala on 2009-11-12
Got a RAID question.  My PC has 2 identical 500gb HDs.  My BIOS setup does not show anything related to RAID, I've checked every entry, every option, yet the 9.10 installer "sees" RAID.

So, is my hardware physically set up as RAID?  How can I check?  I'd like to have it as 2 separate drives, and screw RAID.  What do I do?

---

### Post by Flightmare on 2009-11-13
Then it probably isn't raid if there isn't anything set up in your BIOS. What's the southbridge (chipset) on your motherboard?

---

### Post by Cr0n_J0b on 2009-11-13
Try starting the installer with the nodmraid option.

when you put in the CD/DVD select f6 I think it is for options.  Then choose nodmraid...install as normal.  This should take out the DMRAID stuff.

I've seen some really wierd stuff with 9.10 and the partitioner at install.  sometimes it sees drives, sometimes not.  There have been lots of posts on that...but getting rid of dmraid is a good start.

If you want raid on the boot drives, I think you will need to boot to the liveCD and install mdadm.  once you do that follow the directions to create a md volume and install to that volume.

---

