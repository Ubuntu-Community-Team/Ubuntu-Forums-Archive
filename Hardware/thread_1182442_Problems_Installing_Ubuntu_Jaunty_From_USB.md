---
title: "Problems Installing Ubuntu Jaunty From USB"
date: 2009-06-09
forum: Hardware
---

### Post by binarypill on 2009-06-09
I was dual booting winXP and ubuntu jaunty when I recently ran through the following (arranged chronologically)

1. installed crunchbang as third boot option (after installation, not in grub)
2. corrupted my windows xp (due to resizing the partition)
3. lost grub, could only boot to windows (fixed but still no crunchbang)
4. booted to jaunty only to find out that it was corrupted as well
5. decided to reinstall jaunty from USB and ran on this problem:

"The installer needs to remove operating system files from the install target, but was unable to do so.  The install cannot continue."

-------------------

My partition layout is this:

[ winxp ][ crunchbang ][ jaunty ][/home folder for jaunty]

My grub location is at the [crunchbang]. i suspect this is one of the reasons why i'm having install problems, but i'm not sure.

-----------------

Other suspected problems:

1. I'm using ext4 for jaunty and crunchbang (where the grub is) is using ext3. I noticed I can't access my ext4 partitions from crunchbang.

2. Was using AHCI before I decided to reinstall Jaunty. It was on when I installed crunchbang. I turned it off when I installed winXP (couldn't detect the disk)

3. Hard drive borked (not likely, this machine is just a month old)

-----------------

My machine is an MSI Wind U100 with 2gB RAM, 240gB HD.

Can anybody help?

---

