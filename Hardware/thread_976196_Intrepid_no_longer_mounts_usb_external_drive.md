---
title: "Intrepid no longer mounts usb external drive"
date: 2008-11-09
forum: Hardware
---

### Post by Xitron on 2008-11-09
Brand new install of Intrepid (8.10) on my Dell Latitude D800.  External USB drive that was working fine under 8.04 does not work under 8.10.  I've searched the internet and found many others having this issue, whether it be due to the upgrade from 8.04 to 8.10 or due to the upgrade in the kernel version.  Most hits show a user just trying to mount a USB drive, with the same errors as I am getting.  My situation differs slightly, in that my USB drive is encrypted, although the fact that many people who are not encrypting are having the same issue seems to negate that as the issue.

I plug the drive in, and run the following commands:
cryptsetup luksOpen /dev/sdb1 usb1
mount /usb1

On 8.04 this works flawlessly.  I just tested it on my second notebook running 8.04, so the USB drive isn't the problem.

On 8.10, I get the following errors in my /var/log/messages endlessly, filling the log to a huge size:

sd 2:0:0:0 [sdb] Add. Sense: No additional sense information
sd 2:0:0:0 [sdb] Sense Key : No Sense [current]

This continues until I unplug the device.

This is on my old notebook with is running 8.10.  I will be installing 8.10 on my new notebook as soon as testing on the old notebook proves Intrepid to be safe.  Unfortunately, if I had installed it on my new notebook first and it had this issue, I'd have been unable to do critical backups to the external drive.

I hope that someone at Ubuntu has already addressed this issue and has an easy fix for it.

Thanks!

Unca Xitron

---

### Post by linyanam on 2008-11-12
Please follow the trick here. It worked for me.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789/comments/46](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789/comments/46)

---

