---
title: "need help mounting and formatting Seatec USB external hard drive"
date: 2009-07-24
forum: Hardware
---

### Post by Smiley Coyote on 2009-07-24
I have viewed several threads on mounting externals and each is laden with different sets of advice and it seems that remedying this is different for each user.  For what it is worth, I just installed gpart and it is not showing up there.  

The attachment I have posted shows what comes up when I plug the drive in and here is what comes up when I run sudo fdisk -|:

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf0e5469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6994    56179273+  83  Linux
/dev/sda2            6995        7297     2433847+   5  Extended
/dev/sda5            6995        7297     2433816   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
1 heads, 63 sectors/track, 9922896 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0x01bb4664

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2     9922816   312568672+   7  HPFS/NTFS


I am a pretty serious noob so I would appreciate some stepping down in the technical terms and to any and all helpers, and to those here that have helped me in the past - thanks!

---

### Post by Smiley Coyote on 2009-07-24
*

---

### Post by Smiley Coyote on 2009-07-24
Use the NTFSFIX program.

sudo apt-get install ntfsprogs

sudo ntfsfix /dev/sdb1
(sdb1 or whatever drive the error message indicates)

it worked...got it [here]("http://www.linuxquestions.org/questions/linux-newbie-8/unable-to-mount-usb-external-hard-drive-596525/")

---

### Post by Smiley Coyote on 2009-07-24
Of course, I meant Seagate.  I guess I got the film Sneakers on the brain.

---

