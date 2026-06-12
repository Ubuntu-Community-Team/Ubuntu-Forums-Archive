---
title: "3ware 7006-2 3DM Disk Management Utility"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by icpeanuts on 2007-06-15
I got the 3ware 7006-2 ata raid card with Ubuntu 7.04. I want to find out how to get the 3DM Disk Management Utility to work with Ubuntu. Can someone show me how I can get the utility to work or a way to see the status of the raid. The card works out of the box for Ubuntu 7.04, but it is useless if I don't know what the status of the raid 1 unless I restart the computer.

ANy help would be great. Thanks

---

### Post by bikeman1 on 2007-06-23
There is not an explicit version of 3DM compiled for debian on the 3ware site, but they say one will be coming.  there is source code available if you  want to build your own kernel

while I agree it would be nice to have an array monitor available, for maintenance etc., you can survive well enough without it I think.....if the array is booted up and ready to go, you'll see it listed as an sda device on fdisk. then you can mount it, or partition it, or whatever you like.  If you don't see sda, the array is not built or is not up.  That's one of the nice features of using the 3ware cards with the 2.6 kernel, the array driver is built in.

---

