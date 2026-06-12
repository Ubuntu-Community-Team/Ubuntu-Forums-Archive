---
title: "Managing HDD auto-mount for specific UUIDs"
date: 2012-08-31
forum: Hardware
---

### Post by justinsg on 2012-08-31
Hi there,

I have two identical hard drives that are connected via USB to my Ubuntu 12.04 server box.

I have Samba shares that point to specific mount points for each, and so I have specified these using UUIDs in /etc/fstab as so:
```

UUID=10D88988D8896CB2 /media/external_other ntfs nls=iso8859-1,umask=000  0  0
UUID=D416BE2816BE0B8C /media/external       ntfs nls=iso8859-1,umask=000  0  0

```

The problem occurs when I unplug either of the hard drives. Upon reconnecting the drive (same USB port, without reboot) Ubuntu tries to mount the drive to /media/sdc or /media/sde ignoring fstab. 

It then must follow on with fstab because an error shows on the screen saying that the device can't be mounted to /media/external_other (or external) because it's already mounted to sdc or sdb.

Is there an option somewhere that I have missed?

Cheers,

Justinsg

---

