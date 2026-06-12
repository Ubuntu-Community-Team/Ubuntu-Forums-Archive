---
title: "What is the path to upgrade a single drive system to a RAID 1 system?"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by waynemr on 2009-01-20
My situation is this:
[LIST]
[*]I have a functional 8.10 server using a single 320GB IDE drive that is starting to fail CRC checks on reboot.
[*]I have a PCI-based SATA RAID controller with two 640GB SATA drives (Ubuntu can see these drives, so the controller and drives are functional)
[*]I want to use software RAID 1 on the two 640GB drives as a replacement for the failing IDE drive.
[/LIST]

So, what is the best way to accomplish this? Ideally, I want to setup the RAID array first, make it bootable, and then replicate my existing data/system from the old drive to the new RAID array. Should I just do the standard install a new Ubuntu instance to a RAID 1 array and then copy over everything from the old instance? Or, is there some way to do the migration and the RAID setup at the same time?

Oh, and for the RAID array, I'm guessing I should setup a primary ext3 partition on each drive, as well as an extended swap partition. Then, bind the two primary partitions together in the RAID array and leave the two swap partitions as independent things? I've seen somewhere how you can configure multiple swap partitions in fstab to be load-balanced. In other words, I don't want to make a separate RAID array for the swap partitions, right?

---

### Post by waynemr on 2009-01-21
Well, after a little searching, I located this howto [http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)

It is not exactly what I was thinking about, but I think I can adapt it.

---

