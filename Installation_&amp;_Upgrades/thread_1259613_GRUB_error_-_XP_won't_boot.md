---
title: "GRUB error - XP won't boot"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by HumbleGod on 2009-09-06
I've scoured the available threads, but I haven't found any solutions to this that have worked for me. Any help is greatly appreciated!

I recently upgraded to 9.04, but I had trouble booting from Grub when listing (hd0) as the boot partition (the default option on installation). Eventually I set sdb (the drive with my two OSes) as the boot drive, and things have been working okay - there's a slight lag before booting into Jaunty, and an error message flashed by too quickly for me to read before Jaunty boots, but it does boot. But trying to boot to XP gives me the error "Invalid or unsupported executable format."

The lag/error message when booting into Jaunty is something I'd like to fix one day, but right now I'm more concerned with booting into XP.

fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000014ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   83  Linux

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc543c543

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5737    46082421    7  HPFS/NTFS
/dev/sdb2            8909        9039     1052257+   5  Extended
/dev/sdb3            5738        8908    25471057+  83  Linux
/dev/sdb5            8909        9039     1052226   82  Linux swap / Solaris
```
Note that sda is merely an ext3 disk with media on it. sdb3 is the Jaunty OS partition.

device.map
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

Relevant part of menu.lst
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		64fd1cbe-97ef-42b1-8941-14351f91043f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=64fd1cbe-97ef-42b1-8941-14351f91043f ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		64fd1cbe-97ef-42b1-8941-14351f91043f
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=64fd1cbe-97ef-42b1-8941-14351f91043f ro xforcevesa  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, memtest86+
uuid		64fd1cbe-97ef-42b1-8941-14351f91043f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

I'll gladly post any other info if it might help....

---

### Post by imhotep59 on 2009-09-06
Hello,

Try to change your menu.lst as this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
**makeactive**			
map		(hd0) (hd1)	
map		(hd1) (hd0)	
chainloader	+1

---

### Post by presence1960 on 2009-09-06
Your sdb drive boots first correct? That means sdb is actually (hd0) even though it is labeled sdb. What actually determines disk priority is the order of hard disk boot in BIOS. So your windows entry in menu.lst should be this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1
```

No need for map lines because windows is on the disk that boots first in BIOS! Try that and see if windows boots, if not we need more accurate info about your setup and boot process. Do this:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by HumbleGod on 2009-09-06
> **presence1960 said:**
> Your sdb drive boots first correct? That means sdb is actually (hd0) even though it is labeled sdb. What actually determines disk priority is the order of hard disk boot in BIOS. So your windows entry in menu.lst should be this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1
```

No need for map lines because windows is on the disk that boots first in BIOS! 

That did the trick! For some reason, when I tried booting after doing the edits suggested by imhotep59, my computer spazzed and rebooted itself rather than booting up Windows. (This had happened with other attempted fixes I had tried.) But removing the map commands and changing the drive to (hd0,0) fixed everything. 

Thanks for your help, guys!

---

### Post by presence1960 on 2009-09-06
> **HumbleGod said:**
> That did the trick! For some reason, when I tried booting after doing the edits suggested by imhotep59, my computer spazzed and rebooted itself rather than booting up Windows. (This had happened with other attempted fixes I had tried.) But removing the map commands and changing the driver to (hd0,0) fixed everything. 

Thanks for your help, guys!

Glad you got it working. Enjoy Ubuntu.

This is **why** it worked. Even though fdisk reports your 500 Gb disk as sda and your 75 GB disk as sdb, that is not entirely accurate. When setting up disks & partitions to boot from GRUB it is the hard disk boot order in BIOS that matters. You are booting your sdb disk first so that disk is (hd0) and sda is (hd1). Windows is the first partition on sdb (sdb1). so you have (hd0,0) representing the first partition on the first disk. In GRUB (hdx,y) represents disks (x) and partitions (y). Numbering for disks & partitions starts at 0. That is why it worked. You only need map lines when windows is not on the first hard disk that boots in BIOS. So if windows was on sda you would need map lines because sdb boots first. Windows needs to be on the first disk that boots and the map lines "trick" it into believing it is on the first boot disk.

---

### Post by imhotep59 on 2009-09-07
Thank you for your post, presence1960. I have to say that I didn't know this trick with the "bios order" that is confusing with the "linux order": is it a bug....or a feature ? ;) 
Anyway, I have learnt something new today, thank you again.

---

### Post by HumbleGod on 2009-09-07
Thanks for the explanation, presence. That makes sense, since GRUB always says it's booting from hd0,2 when starting up Jaunty. It is definitely an interesting factoid that BIOS essentially redefines the hd order.

---

