---
title: "Need help using USB"
date: 2012-10-07
forum: Hardware
---

### Post by Sanocon on 2012-10-07
so i installed Ubuntu using an app on another linux os but now my usb went form 8 GB to about 600 MB, it's a micro cruzer 8 GB if you want to know.

so how do i reformat it to have it back to it's normal size?

---

### Post by -kg- on 2012-10-07
> **Sanocon said:**
> so i installed Ubuntu using an app on another linux os but now my usb went form 8 GB to about 600 MB, it's a micro cruzer 8 GB if you want to know.

so how do i reformat it to have it back to it's normal size?

I don't understand how installing Ubuntu using an "app" on another Linux OS would cause a problem with a USB Flash drive, but here goes:

My suggestion would be to first pull up a terminal and execute the command:

```
sudo fdisk -l
```
(with the flash drive inserted, of course)

This will give you information on what partitions are on all hard drives in the computer, the flash drive included.

Since you'll likely have to do so anyway, (install and) launch gparted and see what's on the flash drive.  If you see more than one partition, delete the extra partition, then resize the remaining partition to cover the whole drive.

If all you want to do is gain the memory back, and don't care what's on the drive, delete all of the partitions, then create a new partition covering the whole drive, and format it as desired.  For a flash drive, FAT32 is the best choice, unless you have a specific purpose in mind.

---

