---
title: "Need Help formatting Linux HDD Using Windows Computer"
date: 2018-12-09
forum: Hardware
---

### Post by awskop on 2018-12-09
I'm hoping someone in this community can help me with a hard drive problem.  Recently, I replaced my old laptop (it ran a Linux/Ubuntu OS).  Before getting rid of it, I removed the laptop's hard drive with the intent to repurpose it into a portable hard drive.  I then encased it within a plug and play, SATA compatible enclosure.  Here is my problem:  I want to reformat this drive but every time I plug it into a Windows computer, the WC doesn't even read/register that anything is there/plugged in.  When plugged in, the light on the drive turns on and I can hear it, so I don't think there is anything physically wrong with it.   I started to think that perhaps the Linux Drive might not be compatible with the Windows computer.  Unfortunately, I don't have access to a Linux computer at the moment.  Is there any way to format the LD using the WC?   Step-by-step instructions would be greatly appreciated.  Thanks!

---

### Post by freemedia2018 on 2018-12-10
Administrative tools > Computer management > Storage > Disk Management.

That should give you what you need to set it up for Windows.

It needs to be partitioned as well as formatted.

> started to think that perhaps the Linux Drive might not be compatible with the Windows computer.

That's progress. People used to think the same thing about external drives and GNU/Linux, now they think it's Windows that is incompatible.

---

### Post by yancek on 2018-12-10
Going to Disk Management as suggested should at least show the drive.  If it doesn't show there, check your BIOS to see if it is recognized.  If both those options fail, it might be a bad drive, bad connection or the manner in which it is attached.

---

