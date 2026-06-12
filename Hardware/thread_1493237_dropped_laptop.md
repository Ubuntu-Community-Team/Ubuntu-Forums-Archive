---
title: "dropped laptop"
date: 2010-05-25
forum: Hardware
---

### Post by UncleMonty on 2010-05-25
My dad dropped my laptop. It only fell a few inches onto a wooden floor but I'd like to check it's okay to be on the safe side. According to google I need to run check disk. Is there an ubuntu equivalent of this? If not what can I run to check everything is okay?

---

### Post by tgalati4 on 2010-05-25
Just boot it.  Open a terminal:

dmesg | more   (spacebar to move forward, q to quit)

or

dmesg | grep error

Look for errors.  The filesystem will perform an automatic check (called fsck) if it detects errors.

If you see lots of read errors, then you can assume some disk damage.  You then need to boot with a Live CD.  You can't (or shouldn't) perform an fsck on the partitition that you have booted from.

Once running from the cd, perform fsck on the root partition:

sudo fsck /dev/sda1

Your root partition may be different.  To get a list of devices/partitions:

sudo fdisk -l

Check all partitions with fsck, but you don't need to check /swap.

Don't let your dad near computers.

---

### Post by wojox on 2010-05-25
If you want to run an automatic fsck on next boot, open a terminal and run:

```
sudo touch /forcefsck
```

And reboot.

---

