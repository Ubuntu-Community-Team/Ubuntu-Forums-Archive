---
title: "secure erase"
date: 2015-06-18
forum: Hardware
---

### Post by Vegan on 2015-06-18
I have a hard disk that has a password set. I was wondering if GPARTED can access the secure erase function and recover the disk for refurbishing to a new user.

I will be using a live cd/usb but otherwise disk will be the only hard disk, so it should not be too hard disk

the previous user was malicious and took many steps to prevent refurbishing.

the machine had biometric security enabled too, I was able to get around that only to discover the disk was secured too

definitely a minefield

---

### Post by dino99 on 2015-06-18
normal formatting does not erase the data, but only the table index. So think to do a 'low format' instead.
[http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/](http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/)

---

### Post by NoWayWin8 on 2015-06-19
Secure erase is a feature included in the firmware of the harddrive itself, and the ability to access it depends on how it was configured by the OEM. If the feature is available you can activate it with **hdparm**, and some BIOS's will provide access to secure erase as well.  There's also the **dd** way from a liveCD: ```
# dd if=/dev/zero of=/dev/sda
``` (assuming your hdd is /dev/sda) This will overwrite the entire disk with zeros, depending on the disk size it can take several hours. The process can be done several times for more write cycles and you can also mix it up by doing a cycle with /dev/urandom instead of /dev/zero.

---

### Post by Vegan on 2015-06-21
I tried the hard disk with SeaTools bootable CD, the disk seems to be locked by the BIOS, so I wonder if I need to pull out an older rig or whether to sue the disk make for bricking a disk instead of allowing wiping it

---

### Post by Vegan on 2015-06-21
think the disk is broken, no big deal, got 3 others before i run out and they all work

---

