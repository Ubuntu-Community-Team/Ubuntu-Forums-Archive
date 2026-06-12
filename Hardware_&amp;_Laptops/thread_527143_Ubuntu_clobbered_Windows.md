---
title: "Ubuntu clobbered Windows"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by Jamesinator on 2007-08-16
I originally had Windows ME installed as my OS for the Dell Latitude C600 laptop I've been working on. I installed Ubuntu 7.04 via Live CD and it worked pretty well after booting from GRUB. However, when I try to boot into Windows ME from GRUB I get the following error:

```

Starting up...

Invalid system disk
Replace the disk and press any key

```

Now, this is rather nonsensical as I don't have a floppy drive, only the internal modular bay CD drive. I only have one internal 20g hard drive, which is partitioned with a 10g primary FAT[32] (not sure which) for Windows and a 9g partition for Ubuntu (with 1g for swap).

The boot commands listed for the Windows ME GRUB menu item are:
```

root  (hd0,0)
savedefault
makeactive
chainloader +1

```

Thanks in advance for your help,
~James

---

### Post by kellemes on 2007-08-16
Assuming it's hd0,0 where Windows is..
Is this partition flaged as an active partition? As I remember Windows demands this to be able to boot.

---

### Post by Jamesinator on 2007-08-16
> **kellemes said:**
> Assuming it's hd0,0 where Windows is..
Is this partition flaged as an active partition? As I remember Windows demands this to be able to boot.

Yes, as I stated in my post.

Yes, it does have the "boot" option.

---

### Post by BigBananaMan on 2008-04-29
When you partitioned the drive did you defragment Windows first and then make sure you didn't "cut" the drive with any of the OS on the second partition?  I was limited once to the amount of space I could but on my second partition once because Windows insisted in putting immobile OS data around the middle of the hard drive.  The problems that could come from this is obvious.  You can still access your Windows partition from Ubuntu with the aid of ntfs-3g if there is something important you wanted.

---

