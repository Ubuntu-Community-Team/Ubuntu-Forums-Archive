---
title: "USB Disk mount problem"
date: 2008-10-04
forum: Hardware
---

### Post by psypher on 2008-10-04
Hi all,

these couple of months I have been having a problem with mounting USB disk devices on Ubuntu Hardy. At 1st I thought it was a faulty USB hard drive but I think today I proved that it wasn't. Recently bought a 32GB flash drive and had the exact same problem as with my usb hard drive. It's very random, I can go 3 weeks without a problem and then suddenly for a couple of days on end it's problem after problem. Here's what happens:

Plug in USB drive and nothing happens.
Do a fdisk -l and can clearly see the drive as /dev/sdb1
try and manually mount the drive and get the following error:

mount: special device /dev/sdb1 does not exist

Now here's the weird part. Leave the USB drive in and alone for a few minutes and try the mount again and works perfectly. Now unmount and plug out drive and back in again. Problem back again until you wait a few minutes.

Found a post here: [https://lists.ubuntu.com/archives/ubuntu-users/2008-June/150769.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-June/150769.html) with the same error and the guy there suggested to try:

sudo udevadm trigger

and immediately the USB disk is mounted.

Why is this happening and how could it be permanently fixed.

Note these disk drives are not faulty, this is completely reproducible on various usb drives and the drives mount perfectly on a dual boot of Windows XP on the same hardware.

Thanks

---

### Post by psypher on 2008-10-10
Am I the ONLY person with this problem?

---

### Post by slinkey1981 on 2008-10-10
I have this problem with an 8 gig flash drive, takes about 45 seconds to 2 minutes before it mounts. I *think* it's making you wait while it scans and initializes the drive.


Don't hold me to that though.

---

### Post by thomson2008 on 2008-10-10
Hi. I have run in some problems when mounting external hardisk (and memory sticks) throught usb.When I mount the device, it works well, but after a while, it stops working. After doing a umout -l (if a try just to do moutn I got device busy), I try to mount it again and I got the following error:mount: /dev/usbdisk is not a valid block device.
____________________________________________________
[Find a florist in Phoenix](http://www.florist-flowers-roses-delivery.com/arizona/phoenix_az.html) [cheapest loans](http://www.cheaponline-loans.co.uk/) [casas vilafranca](http://www.vilafrancadelpenedes.com/-1/posts/1_Habitatge/0/) [ringtone downloads](http://www.myringtoneshub.com/)

---

### Post by slinkey1981 on 2008-10-10
> **thomson2008 said:**
> Hi. I have run in some problems when mounting external hardisk (and memory sticks) throught usb.When I mount the device, it works well, but after a while, it stops working. After doing a umout -l (if a try just to do moutn I got device busy), I try to mount it again and I got the following error:mount: /dev/usbdisk is not a valid block device.


What does it say when you use "fdisk -l"?

---

### Post by kpkeerthi on 2008-10-10
> **psypher said:**
> Hi all,

these couple of months I have been having a problem with mounting USB disk devices on Ubuntu Hardy. At 1st I thought it was a faulty USB hard drive but I think today I proved that it wasn't. Recently bought a 32GB flash drive and had the exact same problem as with my usb hard drive. It's very random, I can go 3 weeks without a problem and then suddenly for a couple of days on end it's problem after problem. Here's what happens:

Plug in USB drive and nothing happens.
Do a fdisk -l and can clearly see the drive as /dev/sdb1
try and manually mount the drive and get the following error:

mount: special device /dev/sdb1 does not exist

Now here's the weird part. Leave the USB drive in and alone for a few minutes and try the mount again and works perfectly. Now unmount and plug out drive and back in again. Problem back again until you wait a few minutes.

Found a post here: [https://lists.ubuntu.com/archives/ubuntu-users/2008-June/150769.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-June/150769.html) with the same error and the guy there suggested to try:

sudo udevadm trigger

and immediately the USB disk is mounted.

Why is this happening and how could it be permanently fixed.

Note these disk drives are not faulty, this is completely reproducible on various usb drives and the drives mount perfectly on a dual boot of Windows XP on the same hardware.

Thanks

A quick and dirty way is to put the line ```
/sbin/udevadm trigger 
``` to /etc/rc.local

Requires a reboot for the changes to take effect.

DISCLAIMER: I have not tested this and there probably is a better solution.

---

### Post by psypher on 2008-10-15
No that did not seem to work for me. Still have to run it from the command line once i have plugged in the USB disk, then wait a few mins and it will then mount.

fdisk -l shows the device there but it won't mount manually either

---

### Post by Dan_Dranath999 on 2008-10-15
i have problems with SD cards... one day, they just started mounting as "Read-only" (or not mounting at all) and i haven't been able to fix it.

---

### Post by psypher on 2008-10-15
Today it seems that running udevadm did not fix the issue. i had to run it, wait 5 mins, manually mount the disk, able to access it, umount it, plug it out and plug it back in again and it automatically mounted???

Really damn annoying!

---

