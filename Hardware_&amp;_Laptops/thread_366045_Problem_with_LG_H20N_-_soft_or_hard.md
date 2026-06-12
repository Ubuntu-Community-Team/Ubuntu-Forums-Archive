---
title: "Problem with LG H20N - soft or hard?"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by ispmarin on 2007-02-20
Hello everybody. I posted elsewhere in this forum about a problem with my LG H20N, and after a advise decided to open a new thread. 

I am having some problem with my LG H20N DVD/CD recorder, and I am still not sure if it is a recorder problem, a motherboard problem, or a software/configuration/kernel problem. When I insert a cd/dvd in the drive, automount usually can mount the cd/dvd, but after a LONG time (sometimes 1min!). And then sometimes it fails, and even a manual mount cannot do anything. Sometimes just inserting again the media solves the problem, but sometimes only a reboot will make to read that media (and this happens randomly with different medias (cd, dvd, original, copys, rws, etc etc etc)). The error that appears in dmesg is 

[ 1673.977032] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[ 1673.977039] hda: command error: error=0x50 { LastFailedSense=0x05 }

So i really don`t know what to do. A hdparm on the drive outputs


/dev/hda:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

Any help would be appreciated.

PS: Does anybody knows how to update this driver firmware on linux? 

Thanks.

---

### Post by tgalati4 on 2007-02-20
Sounds like a hardware problem.  Perhaps the laser is weak or out of alignment.  When it heats up it craps out.  Reboot and it cools and works again--for a period of time.

Try booting with a Live CD.  That will give it a workout.

Seek Complete errors means that the drive couldn't read the disk (for any reason.)  It accepted the read request and tried to read the disk but nothing came back.  Bad disk (dirty, sun-exposed, scratched, etc) or bad laser since the mechanical parts of the drive seem to be working.

How old is the drive?  Try putting it in another working machine.  That would isolate the problem quickly.

I recently replaced a new LightScribe drive that would read CD and DVD but couldn't write worth a crap.  Known problem, HP sent a replacement in a week.

Did a Google search on the LG model turn up anything that would relate to reliability?  I didn't see the previous thread so I'm giving blind advice.

Good luck,

Terry

---

