---
title: "Kernel 2.6.24-16-generic borked my boot"
date: 2008-05-16
forum: Hardware
---

### Post by Fatman_UK on 2008-05-16
Hi all.

I just did the upgrade to Hardy, and I'm suddenly getting lots of

```
exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tgo 0 pio 36 in
status: {DRDY}
```

over and over at boot time. There's nothing wrong with the disk, booting a LiveCD and fsck.reiserfs'ing it manually shows no errors. I can even mount the disk normally. Booting with an old kernel (2.6.22-14-generic), I don't get the errors.

Did the latest kernel (2.6.24-16-generic) break ReiserFS somehow?

---

### Post by Fatman_UK on 2008-05-28
I changed the "SATA Mode" setting in the BIOS from "IDE" to "RAID", and the problem went away. **Note:** I am not using RAID. The system didn't reformat my drives or anything. It just wanted the disks in RAID-able mode, I guess.

**WARNING! This might cause your drive names to change! Be sure you can edit your /etc/fstab from a live CD if you do this!**

My drives changed from /dev/sda and /dev/sdb to /dev/sde and /dev/sdf for some reason, which borked my GRUB setup. I booted my usual environment from *Super GRUB Disk* [wonderful tool, recommend recommend recommend] and edited my /boot/grub/device.map to read:

```

(hd0) /dev/sdf
```

and also replaced /dev/sda with /dev/sde in my /etc/fstab.

Hope this helps someone. Good luck!

#include <disclaimer.h>

---

