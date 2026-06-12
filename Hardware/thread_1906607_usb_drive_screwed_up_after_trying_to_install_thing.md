---
title: "usb drive screwed up after trying to install things"
date: 2012-01-09
forum: Hardware
---

### Post by amireldor on 2012-01-09
hello,

not sure if this is the place to ask, but i do want to install ubuntu again :)

i have a 4gb usb drive and i wanted to try out some other distributions. i've downloaded arch linux and 'unetbootin'ed from my windows laptop unto the drive. after gazing at gnome 3 for a few days and realizing i don't like fiddling around with my system all the time (the arch way) i decided to try debian.

after 'dd'-ing debian from arch to the same usb drive, i installed debian and then decided to ditch it and stick to ubuntu. problem is, the 4gb drive shows it only has 650mb of available space! i think something with the debian iso screwed up something in the file system or whatever that is going on inside usb drives.

tried to format from both windows 7 and debian but to no avail. tried unetbootin again and it said 'oh no not enough space on the device'. i'm not sure where to go on from here so i ask for your guidance. thanks!

thanks!

---

### Post by wolfen69 on 2012-01-09
What does Gparted say about the drive?

---

### Post by amireldor on 2012-01-09
I don't have access to a gparted at the moment, I will on the weekend.
As I do have a debian installation available I can use fdisk... I will post the result of the fdisk on the USB drive soon...

---

### Post by efflandt on 2012-01-09
If you dd'd an iso to the usb stick, it probably no longer has a proper partition table, so it only appears to be as big as the read only iso.

With gparted (from Ubuntu install CD or gparted live CD) you could recreate an MSDOS partition table and FAT32 partition which is what Ubuntu Startup Disk Creator uses to create bootable install iso on usb.  I often had to do that when accidentally formatting the entire usb stick (like sdb) instead of the partition on it (like sdb1) in the Startup Disk Creator.

---

### Post by amireldor on 2012-01-11
Thanks for the help!
As soon as I get my hands on a gparted CD I will report back

---

### Post by madvinegar on 2012-01-13
Just use the "disk utility" and delete the partitions and then format it. Simple as that.

The problem you have now is that there has been created a partition of 3.350mb which cannot be formated. As soon as you delete this partition through "disk utility" and format the entire drive, everything will be fixed back to normal.

---

### Post by amireldor on 2012-01-14
Yay, it seems to be working now!

I tried deleting the partition using the default Windows disk utility, but that didn't work because it's Windows. I eventually downloaded some free *Partition Wizard* from here: [http://www.partitionwizard.com/download.html](http://www.partitionwizard.com/download.html) and it did the trick.

I had to make a few attemtps though, but to make a short story shorter, I deleted the partition as madvinegar suggested, created a partition on the whole drive, formatted it as FAT32 and assigned a drive letter because Windows was sad without one. After that, unetbootin was happy and I may now destroy my computer with Ubuntu!

Thanks.

---

