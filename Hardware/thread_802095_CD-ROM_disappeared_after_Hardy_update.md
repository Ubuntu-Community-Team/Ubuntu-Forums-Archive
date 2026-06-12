---
title: "CD-ROM disappeared after Hardy update"
date: 2008-05-21
forum: Hardware
---

### Post by canadianwriterman on 2008-05-21
After one of the recent updates, Hardy no longer recognizes and mounts my CD-ROM (it did before). Any suggestions for how to get it back would be greatly appreciated.

The automatic entry in fstab reads:

/dev/scd0    /media/cdrom0    udf,iso9660  user,noauto,exec,utf8   0   0

---

### Post by canadianwriterman on 2008-05-21
I see lots of other posts with the same problem, but no resolution. I can't believe that all those people have simply accepted that they will no longer have access to their CD drives.

If it helps, I notice that fstab is pointing to /dev/scd0 however, there is no scd0 in /dev.

Anyone have any suggestions? Without a CD drive I'll be forced to go back to Gutsy, but I'd rather stay with Hardy, if possible. Thanks.

---

### Post by HeresJohnny on 2008-05-21
My Compaq Presario V2000 has that same problem, though it seems to work sometimes.  I'm gonna look at it real close tomorrow and see what I can find in the logs.  It seems like the HAL (Hardware Abstraction Layer) is hiccuping when it comes time to initialize the CDROM.  Fwiw, I had the same problem at a lower level of irritation with 7.10.

---

### Post by canadianwriterman on 2008-05-22
Interesting. I believe there was a recent update of HAL, so that may be the problem. 

While I like Hardy overall, there seem to be a few too many issues that belong more in a beta version than a final release. The CD-ROM issue is a big one for me, as I use the CD on this machine in my teaching. The Firefox beta5 crashing issues, especially when on YouTube are another annoyance, and video playback is not nearly as smooth as it was in Gutsy. I'm tempted to reinstall Gutsy.

---

