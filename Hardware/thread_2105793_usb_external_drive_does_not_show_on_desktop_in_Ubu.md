---
title: "usb external drive does not show on desktop in Ubuntu 12.10"
date: 2013-01-17
forum: Hardware
---

### Post by jamarsh on 2013-01-17
If I plug in a usb thumb drive, it shows up in the unity panel and in Nautilus.  However, there is no response from my usb external hard drive.  I know it is recognized, and I can manually mount it.

fdisk -l shows the drive as "Hidden".  I suspect this may be important.

I tried the following instructions found here:
sudo mkdir /media/USERNAME

sudo chown USERNAME.USERNAME /media/USERNAME

with no success

---

### Post by jamarsh on 2013-01-25
I installed Ubuntu 12.10 on a similar but not exact model Acer Aspire laptop with the same result.  I believe this is a bug in Ubuntu 12.10 but cannot find a solution.

---

### Post by jamarsh on 2013-02-23
Well, I think I finally have answered my own question.  For some inexplicable reason, fdisk shows my usb drive as 'Hidden'.  I don't know how or why this happened.  I was able to plug in the drive and have Ubuntu recognize it up to and including Ubuntu 11.10.  12.04 did not work.

I used Gparted to change the flag to Not Hidden.  Now, the usb drive shows up in the Unity launch bar when plugged in.  I hope this helps so other soul out there who has been struggling with this problem.

---

