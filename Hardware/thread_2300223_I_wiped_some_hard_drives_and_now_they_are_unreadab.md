---
title: "I wiped some hard drives and now they are unreadable in windows"
date: 2015-10-24
forum: Hardware
---

### Post by onesojourner on 2015-10-24
I wiped some hard drives using terminal and shred. I then created a new partition table and aligned it to 1 mb. I formatted the drives to ntfs and ubuntu saw them, I made a test folder ect. All was good. Windows does not see that drives at all. What did I do wrong?

Thanks

---

### Post by ajgreeny on 2015-10-24
> **onesojourner said:**
> I wiped some hard drives using terminal and shred. I then created a new partition table and aligned it to 1 mb. I formatted the drives to ntfs and ubuntu saw them, I made a test folder ect. All was good. Windows does not see that drives at all. What did I do wrong?

Thanks
No idea what you did wrong, if anything.

Let's see the output of terminal command ```
sudo fdisk -l
```for a start and we can go from there.

---

### Post by sudodus on 2015-10-24
I suggest that you use mkusb version 10.3 from the ppa:mkusb/unstable to create the partition table and file system. It 'gets everything right' for the drive to be recognized by Windows too. See these links

[mkusb/gui](https://help.ubuntu.com/community/mkusb/gui)

[mkusb#Wipe_menu](https://help.ubuntu.com/community/mkusb#Wipe_menu)

You can select

**b "Big drive: create GUID partition table with NTFS partition" **

if you want an NTFS partition for exchange of data between Ubuntu and Windows.

---

### Post by yancek on 2015-10-24
> I then created a new partition table and aligned it to 1 mb. I formatted the drives to ntfs 

How?  What software did you use to do this?  Windows should be able to see ntfs partitions on an internal/external hard drive but will only see the first partition on a flash drive.  Is that what you are using?

---

### Post by onesojourner on 2015-10-24
I used gparted once I wiped the drives. Unfortunately I shipped the drives out to a customer but I am recreating the issue on another drive right now. I have confirmed they are fine in ubuntu but completely invisible in windows.

---

### Post by sudodus on 2015-10-24
A few weeks ago I tested a lot with gparted and command line methods to create partition tables (MSDOS and GPT) and file systems (ext4, FAT32, NTFS). It may be important that you add a suitable flag depending on how you intend to use the partition. I made automatic methods for the wipe menu of mkusb (post #3).

It works for me directly with gparted unless there is some 'cruft' left in the drive. Wiping the first Mibibyte will usually fix that, and it is also done automatically via the wipe menu of mkusb version 10.3.

---

### Post by sudodus on 2015-10-24
- How were the HDDs used before? (for example as RAID drives?)
- What size are the HDDs?

Please post the output of the following commands:

```
sudo lsblk -fm
```
```
sudo parted -ls
```

---

