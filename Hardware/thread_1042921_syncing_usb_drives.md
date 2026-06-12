---
title: "syncing usb drives"
date: 2009-01-18
forum: Hardware
---

### Post by ringobob on 2009-01-18
I'm trying to set things up such that I have a couple USB flash drives mounted on a central server while I'm at home, then I can just grab them and go when I need to take them with me.

The problem is that they're FAT32 and I don't want to have to remember to sync them every time before I remove them from the system.  Obviously, I don't want to kill the drives with constant writing either.

This is where my knowledge on the subject ends.  If I set up a cron job that syncs every minute, I assume that won't have a measurable effect on USB drive life... if nothing needs to be written, the USB drive will remain untouched, correct?  And if I'm writing a large file/number of files, it shouldn't produce an abnormal amount of wear at that rate, correct?  How would syncing every minute affect the overall system?  This is mostly just a fileserver, with some minor webserving duties... it won't ever be asked to do much more than that.  It's purpose is to keep me learning and using Linux and serve some minor useful purposes... and knowing that I can just yank the USB drive out if I haven't accessed it recently would be very useful.

---

### Post by ringobob on 2009-01-18
I don't know what the policy for bumping threads around here is, hopefully this is kosher.

Ignoring the extra info in my post, my question boils down to 3 points:

1) If I set cron to sync my FAT32 USB flash drive in an effort to avoid doing it manually, if there is no data waiting to be written to the drive will it remain untouched?

2) If I auto sync my drive, what would be an optimal interval that would both minimize drive wear and maximize synchronization?  Is 1 minute going to have an adverse affect on the drive?

3) As I haven't seen a way to specify which drives to sync, auto syncing would presumably have an effect on system performance by forcing more frequent access to the hard drive.  Is this really an issue at scales measured in minutes?  If it is, what kind of performance issues am I likely to see?

Bonus question:
4) Is this the right place for these questions?

---

