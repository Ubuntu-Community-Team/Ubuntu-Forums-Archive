---
title: "USB Flash drive no longer allows writing"
date: 2009-03-27
forum: Hardware
---

### Post by altesk on 2009-03-27
Hello,

I have a USB thumb drive that previously would read and write just fine on my Hardy Heron 8.04 system. For unknown reasons, it began refusing to let me write, the error message saying I lacked permission.

Using Windows XP, I reformatted the drive as FAT32. The problem remains.

I notice that the drive has an owner of root nowadays. I don't know who the owner was back when the drive would read and write correctly.

Is there a setting in Ubuntu that would automatically assign the current user as any USB drive's owner when a drive is connected to the computer?

If not, is there another solution that does not require me to take extra steps every time I plug my Flash memory drive into a USB port?

Based on advice seen in this forum for a somewhat similar problem, I tried using the Terminal to use the sudo and chown commands. I was attempting to change the USB drive's owner from root to the current user. It did not work, but maybe I gave the wrong path describing the drive.

Should I leave the drive owner as root? Each time I connect the drive, should I just use the chmod command to assign read, write, and execute rights to the current user (for all contents of the drive)? If so, I hope you can tell me the exact commands to do it right.

Many thanks in advance for any guidance!

---

