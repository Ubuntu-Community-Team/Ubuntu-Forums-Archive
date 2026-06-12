---
title: "Hard drive partition (FATs)/OS installation help?"
date: 2009-05-03
forum: Hardware
---

### Post by Infran on 2009-05-03
So I have a second HD installed on my computer with Ubuntu.  I want to install another copy of Ubuntu on it so I can boot off of it separately.  I have Intrepid on my first HD.  I'm planning on putting Jaunty on the second one so I can go between the two and try compatibility stuff.

I'm having trouble installing to the second disk.  When I try to use the 'use entire Hard Drive' option, it tells me it can't write the SWAP data (I forget what it called the location, but it had the number '5') and for some reason it will only give me the 'guided installation' option if there's already a partition on the drive.  I tried doing the guided install with a previous, blank partition, and it told me the FATs didn't match.  At this time, I only know how to partition without an install disk or check the partition format type using a Mac.  I tried the 'MS-DOS' format, assuming it might work since I know you can install Ubuntu on a drive with a Windows OS on it, and I thought it might support the format.

The other options for partitioning on my Mac are various Mac Formats, and a UNIX format.

While UNIX sounds most probable, I'd rather not try it only to find out it doesn't work.  (Moving the hard drive between towers takes awhile, even if you don't use any screws.)  So I'm wondering what format Ubuntu uses, if there's an app to format that comes with the Ubuntu 8.10 system and, if necessary, what FATs it uses and how to format *those.*

In case it might be an issue: I actually have the drive in question set to 'master.'  Actually, I think they're both set to 'master.'  So far, it hasn't caused any problems.  I've tried setting it to 'slave,' 'cable-select,' and some other setting - I think it mentioned an RPM limit - that was labeled on the drive.  The installer wouldn't detect the drive as a slave.  Cable-select caused a kernal panic before the OS even booted.  The other option gave me a slew of errors when I tried to start the installer.

If you think the partitioning info will help, please, tell me.  If you think there's something up with the drive, please explain why.  I do have other HDs I could try using if I need to.

---

