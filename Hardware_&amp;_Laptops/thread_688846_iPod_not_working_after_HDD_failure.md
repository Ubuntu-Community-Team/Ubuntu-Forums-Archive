---
title: "iPod not working after HDD failure"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by mlynn5 on 2008-02-05
A few weeks ago the hard drive that held my MBR failed. It was the oldest, with only WinXP on it, so I wasn't too worried about it, apart from the hassle of getting Ubuntu to boot up again.
Since then, though, my iPod can no longer be mounted automatically. I have a feeling that this is due to the change in configuration of my hard drives (old primary slave is now master, old secondary slave is now primary slave). I can mount the iPod from the command line, but I don't really know what I'm doing and the iPod seems to end up as read only when I do so, which is pretty useless. Here's the error message I get when I first plug in the iPod:

Cannot Mount Volume
Unable to Mount the volume 'Mike's iPod"
mount: wrong fs type, bad option, bad superblock on /dev/sdc2, missing codepage or helper program, or other error       in some cases useful info is found in syslog -try dmesg | tail or so
[OK]

"dmesg | tail" tells me:

[43575.404367] sdc: Mode Sense: 68 00 00 08
[43575.404370] sdc: assuming drive cache: write through
[43575.406344] SCSI device sdc: 39075372 2048-byte hdwr sectors (80026 MB)
[43575.407480] sdc: Write Protect is off
[43575.407488] sdc: Mode Sense: 68 00 00 08
[43575.407490] sdc: assuming drive cache: write through
[43575.407496]  sdc: sdc1 sdc2
[43575.488289] sd 2:0:0:0: Attached scsi removable disk sdc
[43575.489024] sd 2:0:0:0: Attached scsi generic sg3 type 0
[43576.977196] FAT: Unrecognized mount option "usefree" or missing value

When I check the properties of the iPod, the Mount Options field in both the Volume and Disk tabs is empty.

I really have no idea how to address this problem. I've looked through all (I think) the GUI OS options presented to me, and I can't find anywhere to fix this.

Any help would be greatly appreciated,
Thanks

---

