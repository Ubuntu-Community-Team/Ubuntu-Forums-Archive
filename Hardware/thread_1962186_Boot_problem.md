---
title: "Boot problem"
date: 2012-04-20
forum: Hardware
---

### Post by n7hor on 2012-04-20
Greetings,  The other evening, my son plugged his USB Seagate GoFlex Drive into my laptop.  Now, when I power on the system I get the following message:  "The disk drive for /media/FreeAgent_GoFlex_Drive is not ready yet or not present.  Continue to wait, or Press S to skip mounting or M for manual recovery."  Senerio 1: If I press "S" the Ubuntu OS boots without any further notices. But if I use my Thumbdrive it will not mount and gives the following error message:  "Unable to mount XYZ_THUMBDRIVE_NAME  Error mounting: mount exited with exit code 1: helper failed with: mount: only root can mount /dev/sdb1 on /media/FreeAgent_GoFlex_Drive"  Senerio 2: If I plug in my sons USB Seagate GoFlex Drive during the: "The disk drive for /media/FreeAgent_GoFlex_Drive is not ready yet or not present.  Continue to wait, or Press S to skip mounting or M for manual recovery." message then the laptop continues the boot process.  Senerio 3: If I power-on/boot with my sons USB Seagate GoFlex drive the boot is normal and I can mount/access my Thumbdrive without any issues.  My sons use of his USB Seagate GoFlex Drive in my laptop seems to have added/modified some files which are read during boot and is not happy when his drive is not present.  How can I correct this issue?  Thanks in advance...tom

---

### Post by oldfred on 2012-04-20
post this:

 sudo cat /etc/fstab

It seems like it may have been added to fstab to auto mount all the time?

---

### Post by n7hor on 2012-04-20
Thanks a lot, That was the problem...tom

---

