---
title: "Formatting external HDD"
date: 2010-12-01
forum: Hardware
---

### Post by BKbroila on 2010-12-01
This should be a quick answer hopefully. I just couldn't find this answer online...
What type should I format a new external HDD, FAT32 or NFTS? I plan on formatting using Windows, not Ubuntu.

---

### Post by runeh76 on 2010-12-01
> **BKbroila said:**
> This should be a quick answer hopefully. I just couldn't find this answer online...
What type should I format a new external HDD, FAT32 or NFTS? I plan on formatting using Windows, not Ubuntu.

Fat32

---

### Post by mastablasta on 2010-12-01
NTFS.
 
the reason is because FAT32 has it's limits in size of the partition as well as in max size of file (i think the limit is arround 2GB or so).

---

### Post by coffeecat on 2010-12-01
> **BKbroila said:**
> What type should I format a new external HDD, FAT32 or NFTS? I plan on formatting using Windows, not Ubuntu.

What are you going to be using it for and what operating systems? Generally speaking, NTFS would be a far better choice than FAT32. It's more modern, more robust and is journalled, so more likely to be repairable in the case of filesystem corruption. Also, FAT32 has a file size limit of 4GB. NTFS will be a better choice for large files.

---

### Post by BKbroila on 2010-12-01
> **coffeecat said:**
> What are you going to be using it for and what operating systems? Generally speaking, NTFS would be a far better choice than FAT32. It's more modern, more robust and is journalled, so more likely to be repairable in the case of filesystem corruption. Also, FAT32 has a file size limit of 4GB. NTFS will be a better choice for large files.

I'm just going to be using it for storing mainly music and movies. And I'd like to use it in both Windows and Linux. So if it's best to format it to NFTS, then I probably don't have to format it, correct (it should be in NFTS already I think)?

---

### Post by coffeecat on 2010-12-01
> **BKbroila said:**
>  So if it's best to format it to NFTS, then I probably don't have to format it, correct (it should be in NFTS already I think)?

I believe most external hard drives (rather than flash drives) come pre-formatted NTFS these days. You can check by plugging it into Ubuntu and looking in System > Administration > Disk Utility. Highlight the drive in the left pane and it will tell you what filesystem in the right pane.

The reason I asked about operating systems is that it gets slightly more complicated if you want to use the drive with MacOS as well. MacOS can read NTFS out of the box, but not write (you have to use ntfs-3g) but since you'll be using only Windows and Linux you should be OK.

---

