---
title: "External memory fails to mount. Help."
date: 2009-04-06
forum: Hardware
---

### Post by ricbritain on 2009-04-06
I am new to Linux having several times tried it very briefly only to abandon it due to minor glitches. I now have **Ubuntueee** on my eeePC and I'm slowly overcoming my previous problems. However I now have a new problem and have failed to find any really helpful info on it. My problem is that almost all my **external USB memory devices fail to mount**. This includes my new Seagate FreeAgent as well as two different Kingston 4Gig USB sticks. I have tried searches in forums but usually get results about problems booting from USBs. SO for this reason I post here. If I can overcome this problem I only have one or two others remaining to make Linux as complete for me as Windows was. 


Thanks in advance.

---

### Post by Gryphon-ni on 2009-04-06
Just read through the following bug report and it seems those who have machines that do not have optical drives can have issues.

See the full bug report here:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/251781]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/251781")



These 2 posts might be of the most relevance



I may have a solution. This may not work for every one.

I installed Intrepid off a bootable USB key, as my laptop has no optical drives.

Today I went through and checked blkid.tab, fstab, and mtab after inserting a USB key and getting the error.

I found a line in blkid.tab that had /dev/sdb1 listed as a CD-Rom device.
There was also a line in fstab to mount /dev/sdb1 as a CD-Rom (I think this was dynamically created when I inserted the USB key).

I removed the line from blkid.tab and modified the line in fstab to have the correct file system.

It now appears to be working.

This is only a workaround as I the line in blkid.tab was no put in manually. I am not sure what created this line.

or...



I had this problem with my Medion Akoya E1210 Netbook. It has no optical drive and it was trying to mount the USB device as a CD/DVD drive on /dev/sdc1. So, I commented out the line in /etc/fstab that would have mounted the CD/DVD drive thus;

#/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

Now my usb devices automount correctly.

---

### Post by ricbritain on 2009-04-08
> **Gryphon-ni said:**
> Just read through the following bug report and it seems those who have machines that do not have optical drives can have issues.

See the full bug report here:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/251781]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/251781")



These 2 posts might be of the most relevance



I may have a solution. This may not work for every one.

I installed Intrepid off a bootable USB key, as my laptop has no optical drives.

Today I went through and checked blkid.tab, fstab, and mtab after inserting a USB key and getting the error.

I found a line in blkid.tab that had /dev/sdb1 listed as a CD-Rom device.
There was also a line in fstab to mount /dev/sdb1 as a CD-Rom (I think this was dynamically created when I inserted the USB key).

I removed the line from blkid.tab and modified the line in fstab to have the correct file system.

It now appears to be working.

This is only a workaround as I the line in blkid.tab was no put in manually. I am not sure what created this line.

or...



I had this problem with my Medion Akoya E1210 Netbook. It has no optical drive and it was trying to mount the USB device as a CD/DVD drive on /dev/sdc1. So, I commented out the line in /etc/fstab that would have mounted the CD/DVD drive thus;

#/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

Now my usb devices automount correctly.

Thanks for the help. Does that mean I should try typing that data in a terminal window?

---

