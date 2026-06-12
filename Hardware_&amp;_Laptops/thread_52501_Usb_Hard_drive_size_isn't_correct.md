---
title: "Usb Hard drive size isn't correct"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by tieflingrogue on 2005-07-28
I just bought a 100G Maxtor Onetouch II USB external hard drive.  Plugged it in, it mounted quickly in gnome but when I checked the drive size (via right click on the drive and check properties), it says that I have 94G of free space.  Is this a format problem or something?

df -T -h gives:  /dev/sda1     vfat     94G  1.4G   92G   2% /media/usbdisk

Thanks

---

### Post by heimo on 2005-07-28
Sounds right. Hard disk sizes are reported in millions of bytes, 100 "GB" of hard disk is 100.000.000 bytes, which translates to about 93 GB. Other way to put it ... (someone will correct me), is to say that hard disk manufacturers are using SI-system, and those 93GB is actually 93GiB, but that's another story.

Size looks right.

---

