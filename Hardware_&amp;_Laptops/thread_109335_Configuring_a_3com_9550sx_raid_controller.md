---
title: "Configuring a 3com 9550sx raid controller"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by BIGtrouble77 on 2005-12-28
I'm having a hell of a time getting ubuntu to recognize my raid array.  This card supports up to 8 drives.  I have 6 300gb drives connected for a 1.3gb raid5 array.

I compiled the driver rather than try to use one of the premade redhat/suse drivers.  The driver appears to be loaded fine, I have it added to the modules list.  Here's the lsmod result:
Module                  Size  Used by
3w_9xxx                36548  0

So I think the driver is loaded properly.  What I don't think is created properly is the block device listing in /dev.  Here's my block device list:
--------------------------------------------
Block devices:
  1 ramdisk
  2 fd
  8 sd
  9 md
 22 ide1
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd
253 device-mapper
254 mdp
--------------------------------------------
I figure the raid controller is represented by the 8, 65, 68, 69, 70, 71, 72, 73 devices and the 128-135 devices.

So I played the guessing game and created a few devices:
mknod /dev/raid b 8 0
mknod /dev/raid1 b 128 0

The only way I could think to check and see if the device is created is through gparted.  Sadly, no new devices named raid(1) show up.  

I also should mention that I'm using my motherboards SATA controller for my system drives(not raided).  Could there be a conflict?  I'm thinking it may be trying to use the same major and minor block device numbers.  If that's the case, does anyone know where in the source those numbers could be changed so I can do a proper recompile?

I'm clearly very limited in this area so I'm hoping some of you can help me out.  I have a very limited understanding of how these types of devices work in linux so I may be missing something very basic.

TIA!
-BT

---

