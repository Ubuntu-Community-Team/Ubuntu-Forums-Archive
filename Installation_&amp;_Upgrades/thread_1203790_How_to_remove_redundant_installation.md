---
title: "How to remove redundant installation"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2009-07-03
Because I didn't really understand what I was doing I accidentally installed Ubuntu onto my hard drive twice.  I want to remove that second installation but can't figure out how.

The current layout is:
/dev/sdb1 ext3
/dev/sdb2 extended
    /dev/sdb6 ext3
    /dev/sdb7 swap (for sdb6)
    /dev/sdb5 swap (for sdb1)

I want to remove sdb6 and sdb7 so I can expand sdb1.  One complication is that grub is looking at the /boot/grub directory on sdb1 and I have not figured out how to reset it to look at the one in sdb1 instead.  I tried issuing:

root (hd1,0)
setup (hd1)

to grub, at the menu prompt, but that did not change the behavior.  So I am afraid that if I just delete the two partitions using gparted, that I will end up with an unbootable system.

---

### Post by Boondoklife on 2009-07-03
Just curious but how are you know the grub command is not doing what you want? also do you want it to boot sdb1 or no?

---

### Post by jcobban on 2009-07-04
> **Boondoklife said:**
> Just curious but how are you know the grub command is not doing what you want? also do you want it to boot sdb1 or no?

I made a trivial change to /boot/grub/menu.lst in the sdb6 partition.  This textual difference is displayed during boot.  Otherwise the copies of menu.lst in the two partitions are identical.  I previously editted menu.lst to manually remove the entries for sdb6, so I am only given the option of booting either from sdb1 or sda1 (WinXP).  Until I resolve this problem I must manually copy menu.lst from the sdb1 partition to the sdb6 partition every time it is modified.

---

