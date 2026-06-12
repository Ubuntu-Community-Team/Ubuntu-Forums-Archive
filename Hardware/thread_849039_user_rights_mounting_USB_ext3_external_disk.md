---
title: "user rights mounting USB ext3 external disk"
date: 2008-07-04
forum: Hardware
---

### Post by nccm on 2008-07-04
I have ext3 formatted a freecom 250GB external USB disk, but can only access it as su.
I think that it is possible to edit fstab, but how can I reach the point where the automatic mounting gives a normal user the rights to access this drive?

The mount information:
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

Thanks for your kind help,
Niels

---

### Post by chewearn on 2008-07-04
After auto-mounting, you run chown.  E.g.

```
sudo chown user:user /media/disk
```

/media/disk
Where the disk got automounted

user
Your username.

---

### Post by nccm on 2008-07-04
Thanks,

It works.
But it should be done automatically when I plug in my usb drive.

Niels

---

### Post by chewearn on 2008-07-04
> **nccm said:**
> Thanks,

It works.
But it should be done automatically when I plug in my usb drive.

Niels

You only need change the owner once.  The disk will "remember" your change, and you don't have to do it in subsequent user automount.

---

### Post by nccm on 2008-07-05
Thank you, I am completely happy.

Niels

---

### Post by simiasota on 2009-05-04
hello,
I'm trying to deal with the same problem.. or almost the same:
I would like to be able to mount the external disk in different linux boxes, where I'm identified by different uids.
Once I chowned the root of the external disk to my uid in that linux box, said it LB1, I would unmount the disk, access another LB (LB2) and automount the disk with complete ownership, even if my uid on LB2 is different from that on LB1.

Should it be possible?

many thanks
francesco

---

