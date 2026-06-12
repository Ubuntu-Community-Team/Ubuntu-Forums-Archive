---
title: "USB problems on ga-ma770-s3 AMD SB600 South Bridge"
date: 2008-06-16
forum: Hardware
---

### Post by lachlanaudas on 2008-06-16
Hi guys I have a nasty problem USB on the GA-MA770-S3 mother board, 
here are the following problem.

My setup is 5 x 500GB external USB hard disks, And 5 internal 1 TB SATA drives on a  GA-MA770-S3 mother board, and extra PCI SATA controler.
Running Ubuntu 8.04 32bit,  Im trying to copy 5 external UBS drive's
to the internal SATA drive's all the same time. As we need to put 5 TB  the internal drives.   Doing this one at the time would take forever.
What happens is the copy starts ok from the external USB  drive,
But once I start the second copy from the external USB drive to the second internal SATA drive, it go's ok for the first 1~100 megs and then
drop's the USB connection to the external drive with a error message "READ ERROR", then Linux Hot plug remounts the same drive as another drive !!!!  Also some of the other USB drives lose there USB mount,, and reconnect as other drive too, needless to say .. you end up with 50+ mounted drives after a short time !!!!..   A real mess ](*,)](*,)](*,)](*,)

I saw some note's about the AMD SB600 South Bridge USB controller being broken, and people trying diff-ant fix's in the kernel, so try-ed the 2.6.25.6 standard kernel..  but with same problems.

Dos any one else know of any fix's  ?  :roll:

Lachlan

---

### Post by Markor on 2008-11-15
It looks like This Bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/260891)

I think that it is something about some bug in SB600 controller hardware.
Also problem occurs if you use devices attached to external USB Hubs.

Try to use Ubuntu 8.10, It should be fixed in it.

Also there is no solution for 8.04 LTS, that I know, Maybe someone
could enlightened me?

---

