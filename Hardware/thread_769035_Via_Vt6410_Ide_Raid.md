---
title: "Via Vt6410 Ide Raid"
date: 2008-04-26
forum: Hardware
---

### Post by fuzzieza on 2008-04-26
Hi,

I've got an Intel motherboard with the above-mentioned controller onboard.  I've set up, with the VIA BIOS two 120GB hard drives as a mirror pair.  This works quite nicely in Windows XP and I see a single drive there that I'd formatted with NTFS.

When I boot Ubuntu, it seems to recognise the individual drives and names them /dev/sda and /dev/sdc; /dev/sdb is a third, non-RAIDed, IDE drive onto which I've installed Ubuntu.  Both /dev/sda and /dev/sdc are correctly shown as having NTFS partitions.

Now, my question is how can I get Ubuntu to understand that this is a RAID/mirror set and actually only one drive.  I'm too scared to mount either of /dev/sda or /dev/sdc in case it ends up being changed and in the process breaking/corrupting the mirror.  mdadm doesn't recognise them as a RAID pair either.

Does anyone know how to make this work?  I've googled around, but there seems to be very little available apart from instructions on how to create a a new software RAID setup; which, of course, would nuke everyting I already have on there.

Any help greatly appreciated,
Andries

---

