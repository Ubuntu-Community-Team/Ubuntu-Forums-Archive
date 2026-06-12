---
title: "exfat sdcard issues"
date: 2020-04-06
forum: Hardware
---

### Post by nodesys on 2020-04-06
I have an exfat 128 GB SD card, and would like to save files into the card. 
My system is ubuntu 19.04.

  Installed exfat-fuse exfat-utils - and the system can recognise the card as read-only.. 
Opened the drive as an administrator - no joy. 
Any clues..? 
Cheers!

---

### Post by TheFu on 2020-04-06
19.04 support ended in January.
Move to 19.10 ASAP.

---

### Post by yancek on 2020-04-06
Did you install the exfat utilities per the recommendations at the site from the below link?  Not sure how you would have done that since 19.04 has been out of support for several months and the repositories have been moved or did you do this in early January of this year?

[https://www.fosslinux.com/17725/how-to-mount-an-exfat-drive-on-ubuntu.htm](https://www.fosslinux.com/17725/how-to-mount-an-exfat-drive-on-ubuntu.htm)

---

### Post by andrew.46 on 2020-04-08
> **nodesys said:**
> I have an exfat 128 GB SD card, and would like to save files into the card. 
My system is ubuntu 19.04.

Kernels 5.4 and above have* native *exfat support which makes life a lot easier...

---

### Post by nodesys on 2020-04-10
i see.
thanks.
will do the upgrade. did not know support has ended :(
cheers!

---

### Post by nodesys on 2020-04-10
However, just to note:
It does mount the drive - just can not save files in the drive.
Will that be solved with linux version 5.4?
cheers!

---

### Post by TheFu on 2020-04-10
I've used exFAT fine using the FUSE tools for 3+ yrs. Never had any issues reading OR writing, though I did avoid using exFAT for personal political reasons.  I wouldn't expect the version added to the kernel to be as solid. Look at the source (who provided it).

As for support vs non-supported Ubuntu versions.  There are LTS and non-LTS releases.  Every 2 yrs, in April, there is an LTS release.  All other releases are non-LTS.  Any release in an odd-year (2021, 2019, 2017, 2015, ....) are non-LTS by definition.  Also, any release in October is a non-LTS, period.  

This month, 20.04 will be released ..... 20 = 2020; 04 = April.  That's an even year, April, so an LTS.  There are rules around how long the LTS gets patches - 3, 5, 10 yrs depending on the ubuntu "flavor".  Ubuntu Server gets 5 yrs of no-hassle support and 10 yrs of some-hassle/paid support.  The main Ubuntu-Desktop running Gnome3 gets 5 yrs of support.  Other desktop flavors get either 3 or 5 yrs of support, but we need to check with those specific project teams about their support plans.  It gets too confusing because the project teams can change their support plans.

For most non-developers, moving from LTS to LTS to LTS is the best plan every 2-2.5 yrs.  Create a calendar entry if you have trouble remembering, like you would for an old friend's birthday.  Never wait passed the support end date.  There are 2 huge reasons for this.  a) being on an unpatched OS leaves your OS hackable. About every 6 months, some remote access attack is uncovered. Just comes down to the luck of timing.  b) Once support ends, migration to the next release is very hard, sometimes impossible, since the repositories are removed.  If you delay, expect to perform a fresh install. Don't expect an upgrade path.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) - note the "standard support" column; scan the entire page, since some critical information isn't at the top.
[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)  - dates/months explained.
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)  - LTS explained.

---

### Post by nodesys on 2020-04-10
Thanks for the reply. Appreciated!
Indeed a fab idea to set reminders - so many things happen :)

The kind of ironic thing is that since i can not use the card to save and back up the computer, upgrading to 20.04 is not entirely a safe option.
There seems to be no way to just remove the exfat and reformat in ex4.
It feels a bit strange in a should not be kind of a way.
Cheers!

---

### Post by TheFu on 2020-04-10
Flash storage should be f2fs, not ext.
```
sudo mkfs -t  f2fs /dev/path/to/sd-device
```
Don't get the device wrong. it is a destructive command.

Need to install the f2fs-utils package first.

I’m pretty big into backups.  Probably 150 posts here about that.  A copy is not a backup.

---

