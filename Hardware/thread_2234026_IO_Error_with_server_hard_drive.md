---
title: "IO Error with server hard drive"
date: 2014-07-12
forum: Hardware
---

### Post by caperrigo on 2014-07-12
I've  recently been having trouble with a hard drive on my server. (by  "recently", I mean problems started about a week and a half ago, and the  server's had about 12 hours of uptime since then)  Whenever I try to  access the contents of the drive, I'm always met with an "Input/output  error" message.  So to give some details:
  
[LIST]
[*]The operating system is Ubuntu Server 12.04.4 LTS


[*]My hard drives are in an LVM configuration, including the hard  drive in question.  The LVM itself appears to work fine, it'll mount all of the  virtual volumes, even one that's located exclusively on the bad drive,  however running "ls -l" on an affected volume yields a series of entries  with unknown attributes, and any attempt at navigating the system is  met with an IO error


[*]Running fsck on both of the mounted filesystems (in this case, the folders mounting /dev/mapper/<device>) returns:

  "Attempt to read block from filesystem resulted in short read while trying to open /dev/mapper/<device>

  Could this be a zero-length partition?"

[*]running any block-level recovery tool like dd or ddrescue spits out a bunch of IO errors

[*]I've tried these attempts both with the drive connected to internal SATA, and through a SATA to USB3 HDD bay, same results

[/LIST]
  I've tried as much as I could find and think of, and still no  results.  Is this drive hosed, or is there still some hope I could  salvage it?

---

