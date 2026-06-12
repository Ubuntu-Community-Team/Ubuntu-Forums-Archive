---
title: "Laptop broke, can't backup Ubuntu partition"
date: 2009-04-09
forum: Hardware
---

### Post by Haruki-kun on 2009-04-09
My Acer unexpectedly died on me. I removed the hard drive and tried to back it up into another computer, but when I plugged it in, the other computer, running Windows, can't see the Ubuntu Partition, where all of my important files are.

I need to recover my files. How can I do this? Do I need a computer running on Linux for that?

Please help me, I'm desperate.

---

### Post by Stupendoussteve on 2009-04-09
If you are using ext3 on the drive, there is a driver available to allow support, either at [http://fs-driver.org/](http://fs-driver.org/) or [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/) - The second one is Open Source but the first one (freeware) works better in my experience.

If you're using another filesystem you will need to boot from a Linux livecd that can write to NTFS, and copy the files to the Windows disk using it. Windows does not recognize Linux filesystems.

---

### Post by Haruki-kun on 2009-04-09
> **Stupendoussteve said:**
> If you are using ext3 on the drive, there is a driver available to allow support, either at [http://fs-driver.org/](http://fs-driver.org/) or [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/) - The second one is Open Source but the first one (freeware) works better in my experience.

If you're using another filesystem you will need to boot from a Linux livecd that can write to NTFS, and copy the files to the Windows disk using it. Windows does not recognize Linux filesystems.


OK, I tried the first one (while downloading a LiveCD in the meantime). I can now see the partition as existant, but Windows says it has no format. It seems to believe the partition is empty. What should I do now?

EDIT: Also, how do I know if a LiveCD can write to NTFS?

---

### Post by FrankT-Qc on 2009-04-09
Why don't you use a live CD to boot your machine, mount your old drive and copy it's content to your good drive ???

have fun

EDIT : Ubuntu LiveCD can write to NTFS

---

