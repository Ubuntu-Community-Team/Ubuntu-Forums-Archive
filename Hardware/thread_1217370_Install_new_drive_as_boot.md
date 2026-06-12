---
title: "Install new drive as /boot"
date: 2009-07-19
forum: Hardware
---

### Post by mickwombat on 2009-07-19
Hi,

I am currently running Ubuntu Server with the /boot partition being on a USB stick as the PC wouldn't boot from the sata drive.

I now have an IDE drive and would like to migrate the /boot partition to this drive.  It has been partitioned etc, and all files transferred across.  I changed the UUID in menu.lst to reflect that of the new drive, but it just won't boot up and returns loads of errors.  The main error is saying that the disk UUID={/ partition} not found.  Even when I put the USB back in and boot up, it returns this error.

If I disconnect this drive, it boots up fine.

What steps do I have to take in order to achieve this?

Thanks

---

