---
title: "Black screen when resuming from hibernate"
date: 2018-01-25
forum: Hardware
---

### Post by ianlynagh on 2018-01-25
Hi all,

I have Ubuntu 16.04.3 on a Dell Precision 5520, using LUKS/LVM to encrypt the disk. If I do "systemctl suspend" then the machine suspends and unsuspends fine. However, if I do "systemctl hibernate" then when I turn the machine back on, after the grub menu and unlocking the disk, I just get a black screen. I've tried a few things, e.g. passing resume=/dev/dm-2 to the kernel, but without any success.

Is this supposed to work? If so, does anyone have any tips for debugging it please?

Here's a little information that might be relevant:

```

# pvs
PV                          VG        Fmt  Attr PSize   PFree
  /dev/mapper/nvme0n1p3_crypt ubuntu-vg lvm2 a--  952.89g 21.57g

```
```

# lvs
  LV     VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   ubuntu-vg -wi-ao---- 899.46g
  swap_1 ubuntu-vg -wi-ao----  31.85g

```
```

$ cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/dm-2                               partition       33398780        0       -1

```


Thanks
Ian

---

