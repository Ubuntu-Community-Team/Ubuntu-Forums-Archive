---
title: "Auto unmount USB drive"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Quicky on 2007-10-31
I have an external hard drive for backup purposes connected to my laptop's dock. Is there a way to automatically unmount the drive when the laptop is removed from the dock? This is the equivalent of essentially just unplugging the USB cable from the back of the machine without ejecting the drive. I'd like to ensure that there's no corruption or data loss and that drive is correctly ejected when the laptop is 'mobile'.

Cheers, Quicky

---

### Post by tech9 on 2007-10-31
I would suggest creating a script and running the script before you undock...

i.e. sudo umount /dev/"your portable HD"

---

### Post by Quicky on 2007-10-31
Thanks, but would that not be the same as manually ejecting (i.e. right-clicking on the desktop icon and choosing 'eject')? I'm specifically wondering if there is something that will unmount the drive automatically prior to the laptop being removed from the dock. For example if my wife decides to use the computer on her knee and just 'unplugs' it from the dock without running ejecting the drive or running any scripts - which she's highly unlikely to remember to do.

Alternatively, I suppose I'm looking for reassurance that there would be no data loss if the drive was simply unplugged without an eject, but I'm not entirely convinced that's the case.

Perhaps I should simply turn off automounting? What d'you reckon?

---

### Post by tech9 on 2007-11-01
> **Quicky said:**
> Thanks, but would that not be the same as manually ejecting (i.e. right-clicking on the desktop icon and choosing 'eject')? I'm specifically wondering if there is something that will unmount the drive automatically prior to the laptop being removed from the dock. For example if my wife decides to use the computer on her knee and just 'unplugs' it from the dock without running ejecting the drive or running any scripts - which she's highly unlikely to remember to do.

Alternatively, I suppose I'm looking for reassurance that there would be no data loss if the drive was simply unplugged without an eject, but I'm not entirely convinced that's the case.

Perhaps I should simply turn off auto-mounting? What d'you reckon?

I can confirm that if you do not manually unmount the device that data can be lost. I have tested this and the data did not save... not sure about an automatic unmount... you may just want to turn the auto-mount feature off then.

---

