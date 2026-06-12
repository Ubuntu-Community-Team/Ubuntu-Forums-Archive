---
title: "New external harddrive: best filesystem to format it to"
date: 2012-08-04
forum: Hardware
---

### Post by Superpelican12 on 2012-08-04
I have a new Toshiba StorE Alu 500GB harddrive which came formatted in NTFS. Ubuntu recognizes it (and I've already deleted some and moved some files that came with the hard drive). So I suspect everything' s fine. But I don't know if I should format it to Ext2/3/4 or Brtfs. It will only be used as backup of data. I've read that it seems to be better to format a SSD drive as Ext2 (with as argument that Ext4 does more write operations and that should be bad for flash memory), I don't know if this is true for the modern SSDs (or any SSDs). However I don't know if there is a preferred file system for external USB drives. Should I leave it as NTFS or reformat to something else?

---

### Post by ahallubuntu on 2012-08-04
The reason ext2 was recommended for SSD drives was to eliminate unnecessary writes to the SSD that a journaling filesystem like ext3 or ext4 would do.  This is not a consideration with a regular hard drive.

If you will ever use your new external drive with a Windows system, leave it formatted to NTFS.  If you will NEVER use this new drive with Windows, I recommend you format it to ext4.  You will get better performance in Linux with a native file system especially when copying very large files.

---

### Post by Cheesemill on 2012-08-04
> **ahallubuntu said:**
> If you will ever use your new external drive with a Windows system, leave it formatted to NTFS.  If you will NEVER use this new drive with Windows, I recommend you format it to ext4.  You will get better performance in Linux with a native file system especially when copying very large files.
+1

If it's only ever going to be used with Linux then format it as ext4.

If you need compatibility with Windows machines then use NTFS.

---

### Post by oldfred on 2012-08-04
If you are backing up just your own data NTFS will work if you have Windows. You want the journal that NTFS has but have to have Windows to occasionally run chkdsk. Ubuntu automatically runs fsck on / every 40 or 60 reboots, Windows does not so you have to manually do it.

But NTFS does not support ownership & permissions, so any system configuration or the hidden files will not preserve those settings. You can preserve settings if you do not just copy but use a compressed format like tar to backup system settings & data. But still better to use ext4, then for any Linux backup.

---

