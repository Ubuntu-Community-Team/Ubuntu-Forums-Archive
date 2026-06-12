---
title: "Repair MBR"
date: 2008-09-24
forum: General Help
---

### Post by gr8npwrfl on 2008-09-24
I lost my boot drive to a hardware error.

I did have everything backed up.

I have Ubuntu 8.04 in a directory on my third drive.

So my path is (hd2,0)/ubuntu/disks/

My grub file is (hd2,0)/ubuntu/disks/boot/grub/menu.lst

If I try and reinstall grub from a live CD it can't find
the menu.lst file. From within grub I have even tried
"find /media/Local Disk/ubuntu/disks/boot/grub/"
It says can't find file.

Because Ubuntu is installed in a Windows directory how
do I repair the grub boot loader ? I have a the files that
were backed up and reinstalled in their directory.

I had to manually edit the menu.lst file as while I put in a
new primary drive, I also added a secondary drive that pushed
my Ubuntu drive to number 3. So I changed the menu.lst file
from (hd1,0) to (hd2,0).

I just can't find out where to go from here as none of the
articles that I have read deal with Ubuntu on an NTFS Partition.

They won't allow me to have a Linux partition, I have to run
Ubuntu this way as it was the only concession they would allow.

---

### Post by thefoolnz on 2008-09-24
Hello,

you would need to put the ubuntu / grub files on to a common file system so that ubuntu/windows/grub loader can read from it at least so putting your configuration files onto an ntfs partition wont work well as grub currently does not have any native ntfs file system support you would do better by placing the files onto a fat file system which is supported by all the componets

hope that helps

---

### Post by gr8npwrfl on 2008-09-24
Wubi installed the system this way.

So if grub can't access an NTFS system why did it work
for over a year with the menu.lst file on the NTFS partition ?

Or am I mistaken that Wubi sets up a grub boot loader.

All my partitions are NTFS even the boot drive was.

---

### Post by gr8npwrfl on 2008-09-24
I did not realize that Wubi is its own boot and moved this question to the proper forum

---

