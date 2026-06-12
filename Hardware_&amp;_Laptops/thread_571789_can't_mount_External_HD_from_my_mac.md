---
title: "can't mount External HD from my mac"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by craigsharp on 2007-10-09
Ok,  My powerbook went completely out the other day, luckily I had everything backed up on an external hard drive.  Now i am trying to figure out how to get all the information off of the HDD onto my ubuntu machine.  I plug it in and nothing happens.  When I ```
sudo fdisk -l
```
this is what I get ```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/hda2           12749       14424    13462470   83  Linux
/dev/hda3           14425       14593     1357492+  82  Linux swap / Solaris

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

```

Any suggestions?  Oh and when I go to /dev/disk/by-id/  I can see "usb-Maxtor_6_L120P0-0:0"

Please Help!


Thanks
Craig

---

### Post by craigsharp on 2007-10-09
bump bump

---

### Post by craigsharp on 2007-10-10
anybody have any idea?  Should I post this in another category?

---

### Post by Xenaco on 2007-10-10
How did you backup everything to the external hard disk?  What software (operating system and program) did you use?

If you did a simple 'dd' backup of your disk to the external disk you can boot a liveCD version of Ubuntu (Kubuntu or Xubuntu) and then restore the backup from the external disk.

This restore will be totally dependent upon how and what you backed up on the external hard disk.

Restoring your system is dependent upon what information is on the backup.

---

### Post by craigsharp on 2007-10-11
As stated earlier, I used my mac with osx.  All I did was plugged it in and copied my user folder over to the hard drive.  I'm assuming it is in mac format.  I did get my info off though,  I downloaded the trial of MacDrive for blasted windows and it worked without a hitch.

---

