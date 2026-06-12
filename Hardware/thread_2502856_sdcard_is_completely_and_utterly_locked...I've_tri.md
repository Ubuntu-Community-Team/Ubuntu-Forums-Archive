---
title: "sdcard is completely and utterly locked...I've tried all I can think of"
date: 2024-12-02
forum: Hardware
---

### Post by 98cwitr on 2024-12-02
Have an SDcard running Manjaro-ARM, and after doing a distro update it nuked itself and won't boot. Happy to wipe it and start over, but can't even do that.

Things I've tried

1. shred command
2. dd if=/dev/zero (with and without bs=446 to wipe the MBR)
3. using disks util in gui
4. usb startup creator (GTK)
5. e2fsck -y /dev/sda 
6. Tried to wipe with my android phone
7. Tried gparted

No errors in any of the above except #5, says it can't set superblock (tried e2fsck -b 8193 and 32768) . Everything seems to take, but everything is still there; partitions, files and all...even sda2 and sda3 are still mountable and readable.

I also tried rewriting permissions on /dev/sda and /dev/sda3 (main partition with the OS and data)

Drive layout:

/dev/sda1 - unknown
/dev/sda2 - U-Boot partition
/dev/sda3 - Main partition with OS

Any help would be greatly appreciated. A 256GB card is cheap these days, but I'm trying to get this back up and running ASAP.

---

### Post by VMC on 2024-12-02
The slider on the side. Is it damaged? I had to use tape to make mine read/writable again

---

### Post by 98cwitr on 2024-12-02
> **VMC said:**
> The slider on the side. Is it damaged? I had to use tape to make mine read/writable again

No slider...it's a micro (sorry, should have specified that)

---

### Post by Autodave on 2024-12-03
Usually, a superblock error is the end of the card.  Have you tried accessing it from both Windows and Linux?  I have, on rare occasions, been able to access card or USB stick by refrigerating it for a hour or so and then quickly trying to read it or reformat it.  Even if you manage to get it to work again, don't trust it.

---

### Post by 98cwitr on 2024-12-03
> **Autodave said:**
> Usually, a superblock error is the end of the card.  Have you tried accessing it from both Windows and Linux?  I have, on rare occasions, been able to access card or USB stick by refrigerating it for a hour or so and then quickly trying to read it or reformat it.  Even if you manage to get it to work again, don't trust it.

yeah Im letting testdisk do its thing right now. It is seeing errors. I'll try the freezer thing, all else fails

---

### Post by yancek on 2024-12-03
Is this a full install of Manjaro on that disk?  Did you see any errors/warning messages during the upgrade?  When you run fdisk or parted -l on that drive, does it show sda1 as unknown?  You have a boot and system partition, would sda1 be your EFI or is this a Legacy install?  What filesystem type is on sda2?

You run e2fsck on the filesystem which is on the partition, /dev/sda3 sda2 not sda.

If you want to just start over, did you have any luck when you used gparted to create a new partition table on the device?  That doesn't wipe data but does make it very difficult to access.

---

### Post by 98cwitr on 2024-12-05
@yancek

Thanks for the questions! Here's a screenshot of parted and gnome disks output. The free space sections are quite strange, but if I recall, they were still present when this was working. Yes, it was a full install of Manjaro-ARM on /dev/sda3, uboot to handle the board.

 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=294606&stc=1[/IMG]

No luck on additional attempts to wipe. gparted does this

First, I delete all the partitions, and apply those changes. Everything looks good.


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294608&stc=1[/IMG]

Then boom...target remains (completely unchanged and unphased):
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294607&stc=1[/IMG]

---

