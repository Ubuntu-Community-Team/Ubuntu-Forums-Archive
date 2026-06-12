---
title: "Restoring corrupt LVM partition"
date: 2010-04-10
forum: Hardware
---

### Post by JakeWins on 2010-04-10
My ubuntu server 9.04 is unable to boot after a recent power failure. The problem appears to be with meta-data for one of the partitions. I'm not very good at hardware, so I'm kind of in the dark here, and hoping someone here can give me some hints.

The latest backup is over a week old, so I'm really hoping to be able to restore the drive.

I found a guide on the subject from Novell, and though it did seem to shed some light, it was not able to resolve the problem. Here are some things I learned about the state of the system while trying that:

```

root@ubuntu:/dev# cat /proc/partitions 
major minor  #blocks  name

   7        0     684016 loop0
   8        0  117246528 sda
   8        1  116993331 sda1
   8        2          1 sda2
   8        5     248976 sda5
```

```

root@ubuntu:/dev# pvscan
  Couldn't find device with uuid 'tRBUrH-ybeu-cg9r-uJp6-vKoL-y3oK-UEfbRn'.
  Couldn't find device with uuid 'tRBUrH-ybeu-cg9r-uJp6-vKoL-y3oK-UEfbRn'.
  PV /dev/sda1        VG bitchware   lvm2 [111,57 GB / 0    free]
  PV unknown device   VG bitchware   lvm2 [465,76 GB / 232,88 GB free]
  Total: 2 [577,33 GB] / in use: 2 [577,33 GB] / in no VG: 0 [0   ]
```

```

root@ubuntu:/dev# vgchange -ay
  Couldn't find device with uuid 'tRBUrH-ybeu-cg9r-uJp6-vKoL-y3oK-UEfbRn'.
  Couldn't find all physical volumes for volume group bitchware.
  Couldn't find device with uuid 'tRBUrH-ybeu-cg9r-uJp6-vKoL-y3oK-UEfbRn'.
  Couldn't find all physical volumes for volume group bitchware.
  Volume group "bitchware" not found
```

```

root@ubuntu:/dev# pvcreate --uuid tRBUrH-ybeu-cg9r-uJp6-vKoL-y3oK-UEfbRn /dev/sda2
  Device /dev/sda2 not found (or ignored by filtering).
```

If anyone has any clues or good links, please share :)

---

