---
title: "CD drive sticks"
date: 2009-02-03
forum: Hardware
---

### Post by lsutiger on 2009-02-03
I have a problem with my CD drive sticking after I write to a CD/DVD. Once all data is written and the computer ejects the media, I can tap the cd drawer for it to recall, but after that, I can not open it. The only fix is to reboot.

When I try  eject /dev/scd I get  unable to find or open device for: `scd', eject -v scd0, I get this:
```
eject: device name is `scd0'
eject: expanded name is `/dev/scd0'
eject: `/dev/scd0' is not mounted
eject: `/dev/scd0' is not a mount point
eject: `/dev/scd0' is not a multipartition device
eject: trying to eject `/dev/scd0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: trying to eject `/dev/scd0' using SCSI commands
eject: SCSI eject succeeded

```

 When I go to computer, CD/DVD drive right click and eject I get "unable to mount media, there is probably no media in drive."

I can eject with the 'emergency' eject on the front of the drive, but it is a fight.

Any ideas?

---

