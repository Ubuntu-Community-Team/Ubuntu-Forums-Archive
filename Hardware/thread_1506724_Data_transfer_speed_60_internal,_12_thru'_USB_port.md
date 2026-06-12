---
title: "Data transfer speed 60 internal, 12 thru' USB port???"
date: 2010-06-10
forum: Hardware
---

### Post by Moozillaaa on 2010-06-10
Does this sound correct? 

By 'internal', I mean from SATA channel x to SATA channel y. 

Through an external enclosure, IDE drive, any USB port, to any internal SATA drive, transfer speed is 1/5th as fast.

Sometimes my boot hangs at 'loading hardware drivers'.

Do I have driver conflict? Where should I look?

---

### Post by jml on 2010-06-10
Generally internal transfer rates are faster than "external"  By the way, are you using USB 1.0 or 2.0?  1.0 only has a transfer rate of 12 Mbits per second versus 480 Mbits per second for USB 2.0.

Joe

---

### Post by Moozillaaa on 2010-06-10
It's 2.0.

Would driver errors make it default to 1.0 speed? How could I find out?

---

### Post by Joe of loath on 2010-06-10
The maximum transfer rate I've ever got from USB 2.0 is 22Mb/s. USB 1.0 something closer to 800Kb/s. However, what you're transferring to/from makes a difference. From my experience on my PC, a cheap USB stick is 3Mb/s write, An expensive one 6Mb/s, a cheap SD card 4Mb/s and a USB hard drive 22Mb/s.

---

### Post by Moozillaaa on 2010-07-02
I'm going from a USB enclosure with an IDE drive - WD 250G drive, to an internal SATA drive.

---

### Post by nmaster on 2010-07-03
from [http://ubuntuforums.org/newreply.php?do=newreply&p=9541014:](http://ubuntuforums.org/newreply.php?do=newreply&p=9541014:)
> **Moozillaaa said:**
> I see the same thing as the OP, with respect  to USB transfer speed.

What hardware do you have?

My USB Xfer rate is 12mb/s, with internal speed around 60mb/s.

Post [here]("http://ubuntuforums.org/showthread.php?p=9541000#post9541000") if you have ideas please...

well to be honest 30MB/s is more of a peak value.  usually its in the  mid to high 20s.  i'm not completely sure what you problem could be, but  it might be the filesystem(s).  i have ntfs on my external  and ext4 on my internal drive. i noticed better (faster) performance when i reformatted my internal drive to ext4 (from ext3).

also, have you tried actually benchmarking it? perhaps with iozone or fio (both in the repos).  it might just be that the gui is displaying the wrong numbers.

---

