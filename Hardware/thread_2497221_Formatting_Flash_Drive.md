---
title: "Formatting Flash Drive"
date: 2024-04-27
forum: Hardware
---

### Post by daniell59 on 2024-04-27
I need to format my 64 GIG flash drive. What file system should I use?

---

### Post by yancek on 2024-04-27
What are you going to use if for?  If you are going to use it with both Linux and windows you will need to use a windows filesystem as a default windows system does not understand Linux filesystems.  If you are going to use it only on Linux, ext4 is a standard used on Linux systems.  There are a number of different filesystems available and you will need to determine what is best for you depending on usage.

---

### Post by TheFu on 2024-04-27
For flash media used for data, there are two real choices today.
[LIST]
[*]**f2fs** for linux only data that will only be accessed from Linux systems you control.
[*]**exFAT** for general data used by many different OSes.
[/LIST]
To safe writes to the flash chips, neither of those file systems are journalled.  That is a liability for data loss. It may be best to take the extra write counts and use a journalled file system like ext4 instead.

If you want to run/boot Linux off the flash drive, then things are more complex. If you have a Linux ISO, then the file system is built-into the ISO itself.

---

### Post by daniell59 on 2024-04-28
I checked the 64GB flash drive in G Partition. It is formatted in FAT32. How is that possible? I thought that would far exceed the limit.

---

### Post by TheFu on 2024-04-28
> **daniell59 said:**
> I checked the 64GB flash drive in G Partition. It is formatted in FAT32. How is that possible? I thought that would far exceed the limit.

FAT32 only has a limitation due to MSFT changing their code to force it.  Linux doesn't have any size limitation for FAT32, but FAT32 is a really bad choice for a file system, unless it is mandated by some other device, like a camera.  I think MSFT made 64G the limit on FAT32.  The file system was designed when massive storage was just 4GB in size.  It was never meant to be used with more than that amount.  The allocations become wasteful.

But you asked which were the best choices. My other reply provided the answer.  No way should you leave it as FAT32.  THAT would be a terrible choice for flash storage these days for a number of reasons.

You can use wikipedia to find a table of file system comparisons.  You want something reasonably popular, reasonably without flaws that will lose your data, without journaling to avoid too many write cycles on the flash media.  Hence, my recommendations of either f2fs or exFAT.

---

### Post by yancek on 2024-04-28
The 4GB limitation is the maximum file size.  You can find more details on it at the site at the link below or doing a simple online search to find other sites. 

[https://www.reddit.com/r/DataHoarder/comments/11nka02/ntfs_fat32_exfat_file_systems_and_their/](https://www.reddit.com/r/DataHoarder/comments/11nka02/ntfs_fat32_exfat_file_systems_and_their/)

---

