---
title: "udev not persistent mapping devicecs"
date: 2014-07-04
forum: Hardware
---

### Post by Jeff_Parke on 2014-07-04
hi,

I have two BD-ROM drives in my system, same make, bought at the same time.

Since I upgraded ubuntu last month, I'm finding that when the system boots, it doesn't consistently map the drives to the same device, i.e. /dev/sr0 and /dev/sr1 sometimes swap over.

I'd like to write a udev rule to fix this. I'm running:

```
udevadm info /dev/sr#
```

and the only difference I see is in serial number, as you might expect:

> E: ID_SERIAL=ATAPI_BD_O_DH4O3S_0040F002018000F3F301
E: ID_SERIAL=ATAPI_BD_O_DH4O3S_0040F00201800074F301

I've experimented with creating a new udev rule in /etc/udev/rules.d/90-local.rules

> SUBSYSTEM=="block",ATTR{id_serial}=="ATAPI_BD_O_DH4O3S_0040F002018000F3F301", NAME="sr11"

The rule seems to be read with no complaints when I reload udev, so I guess it is syntactically correct. I think it should then map one of the drives to /dev/sr11, but /dev/sr11 does not appear :(

What am I missing?

many thanks,

Jeff.

---

### Post by bashiergui on 2014-07-14
If you want the bluray disk drive to mount in the same spot persistently, use fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

