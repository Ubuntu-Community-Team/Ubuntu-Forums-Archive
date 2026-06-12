---
title: "Help to Create UUID for ReiserFS Partition"
date: 2008-05-09
forum: Hardware
---

### Post by c3apollyon on 2008-05-09
I'm having the very odd problem of having my /home partition being re-ordered /dev/sdc3 or /dev/sde3 randomly on different boot-ups - translating into an error during the boot process whenever the computer decides to render the boot partition the opposite of how it's described in /etc/fstab.

The obvious route around this is to create a UUID for this drive, however, it is the only drive that does not have one automatically generated for it in /dev/disk/by-uuid.  I've used the uuidgen command to create a random UUID and tried to use reiserfstune to apply it to my partition but I receive an error (something about the 3.5 format?)

Can anyone with knowledge about uuids and reiserfs pipe in to help me out on this front?  Or does anyone know why Ubuntu is reordering my drives.

Thanks.

Jason

---

