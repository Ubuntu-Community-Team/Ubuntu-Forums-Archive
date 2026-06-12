---
title: "Problems mounting a Sata2 disk"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by Regenerate on 2006-07-07
Hi all,

I tried installing Ubuntu on my Sata2 disk but the controler on my motherboard (see below for specs) isn't supported by the 2.6.15 linux kernel that's in the dapper release (it's supported on 2.6.16 kenrels and newer). So I plugged in a IDE disk besides the Sata2 disk, and installed Ubuntu. I also upgraded to all latest versions and also installed the linux-image-2.6.15-25-k7. 
After all that I could see the sata2 disk being detected bij the system and I used QTParted to format the disk and make an ext3 partition on it.

I used sudo mkdir /media/data to make a directory. In system settings I configured the disk as being of the type Ext3, mountpoint /media/data, station /dev/sda1, activation on startup and writable are both enabled. Mount permission is for root only. The disk has also been activated.

Now I can go to the /media/data folder (to see a locked lost+found folder in it) but I can't do anything with it. Can't place files in it for example, if I try I get an Access Denied message. I also tried differet Mount permission settings, but those don't seem to make a difference.
When going to media:/ (or system:/media) I can see the sata disk next to the IDE disk, mounted and all. When looking at the properties I can see the exact same settingings for both disks.

Anybody who can shed some light on my problem?

Thanks in advance!

---

