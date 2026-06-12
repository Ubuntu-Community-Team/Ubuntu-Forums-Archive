---
title: "gparted can't see my partitions"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by topnob on 2007-08-29
Hi,

I have been looking for a solution for this problem, but have not found anything remotely like it so far, so I'm going to ask it here, if there is a better place or its already been solved, thats great and I have no problem removing this topic, because I just want to fix it.  

Ok then the problem is gparted can't see my partitions, it says my whole drive is unpartitioned.  However if I run fdisk I get the full partition list no problems.

I am running Ubuntu as my primary system, but i have the initial install of windows, shrunk and not yet installed(still on that OEM welcome to windows click next blah).  I also left the dell partition, but created 4 new partitions, 1 swap, 4 ext3 partitions(equal to the 8max, including the extended part).  On the first ext3 partition I installed Ubuntu, and on the second I installed PCLinuXOS just to see what it was all about, the third partition was going to be another test bed distro spot, the final one just has shared things like music and stuff.  

So everything went fine with the the install of both Ubuntu and PCLinuxOS(had to make some grub changes as PCLinuxOS wiped the ubuntu GRUB) but after that I tried to install Mandriva and thats when it said there was nothing on the drive.  Weird I though, so I rebooted into Ubuntu and there was no partitions listed in gparted.  But as I said above there is if I run fdisk.  

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        1817    14530792+   7  HPFS/NTFS
/dev/sda3            1818        2078     2096482+  82  Linux swap / Solaris
/dev/sda4            2079       14593   100526737+   5  Extended
/dev/sda5            2079        3354    10249438+  83  Linux
/dev/sda6            3355        5917    20587297+  83  Linux
/dev/sda7            5918        8468    20490876   83  Linux
/dev/sda8            8469       14593    49199031   83  Linux

I'm hoping theres an easy fix, and no I don't want to wipe the disk and start again its why I don't run windows any more, amongst the many other reasons.

Thanks in Advance for any help.

---

### Post by merlinus on 2007-08-29
Have you tried gparted live cd?

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by topnob on 2007-08-29
No will try it when I get home, but(not sure if I mentioned it) the weird thing is everything works, I can boot into Ubuntu or PCLinuxOS fine, just can't see the partitions with anything but fdisk.

---

### Post by topnob on 2007-08-31
Ok no good, I have also noticed, that my Ubuntu Freezes, and I've worked out that it can't access the swap partition either.  its weird.

---

