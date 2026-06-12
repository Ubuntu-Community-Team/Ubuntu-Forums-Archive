---
title: "USB 2.0 External HD"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by arbeck on 2005-03-05
I have an external USB 2.0 HD that i'm trying to use.  I know the drive works because I've tested it on windows XP and Mac OS X.  When I plug it in under Ubuntu it doesn't automount or show up any where as being connected.  dmesg gives me the following:

usb 3-6: new high speed USB device using address 3
usb 3-6: device not accepting address 3, error -71
usb 3-6: new high speed USB device using address 4
usb 3-6: device not accepting address 4, error -71

My motherboard is an Abit NF7-S 2.0, which is an nforce2 chipset.  I am able to mount a USB 1.0 camera as an external drive without any problems.  I'm running the standard warty kernel.  Any ideas?

---

### Post by dikki on 2005-03-06
I read your problem and typed "usb hd" to the search bar, because I have an USB device, too, but I didn't use it yet under Linux, but wanted to try out. I found a reply:

> USB issues
----------

Some users experience problems with USB communication. There are some
hardware USB controllers which is problematic. This might be caused
by either electrical properties of the bus, or by badly programmed
drivers in the host kernel.

nForce 2 motherboards are known to be problematic.
You don't have one of these do you. Also, if you have one, maybe try a powered usb hub, sometimes they will work a little better. 

But I powered on my HDD, and it would work, but it is formatted to NTFS. Try adding this to your /etc/fstab, anyway:

/dev/sdb /mnt/usb0 auto rw,user,noauto,uid=digitalpure 0 0

(might be /dev/sdb1 )

---

### Post by dikki on 2005-03-06
It works for me! I had to use 

/dev/sda1 /media/windows ntfs rw,user,noauto,umask=0222 0 0

after installing ntfstools, ntfslib5 etc.; and "mkdir /media/windows".  However, it was my problem, I hope you'll find solution to yours, too.

---

### Post by arbeck on 2005-03-06
dikki,

you're solution isn't going to work for me because the HD doesn't get put into dev when it is plugged in.  It's not there for me to mount.

This HAS to be a driver issue between the USB driver for my hardware in this kernel.  I'm looking to see if anyone else has had this kind of problem and what they did to solve it (i.e. upgrading the kernel)

---

### Post by alastair on 2005-03-06
You could check here :

[http://www.linux-usb.org/FAQ.html](http://www.linux-usb.org/FAQ.html)

It does mention the "device not accepting address" problem.

---

