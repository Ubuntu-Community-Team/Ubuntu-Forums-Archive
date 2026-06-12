---
title: "Best filesystem for mp3s"
date: 2010-03-28
forum: Hardware
---

### Post by charding on 2010-03-28
Hi,

I'm in the process of getting an external harddrive for the purpose of storing my mp3s and sharing on bittorrent.

I've read that, depending on what you think is a 'large' or 'small' file, mp3s could be classified as large files and xfs and/or ext3 may be the best file system type for this drive. 

That being said, since there won't be many updates to this drive/filesystem (mostly read operations), I don't really need a journaled option. I know I can switch off noatime and modify the 'data' variable in fstab, but is there a filesystem that has better read operation over the other?

Any input would be appreciated.

Thanks,

---

### Post by 2hot6ft2 on 2010-03-28
ext3 over xfs. And when you say large files what comes to mind is 4GB files in which case NTFS. but if it's not going to have files that large and it's only going to be used with linux then ext3 should be fine. You may consider ext4 as well but I would look into that first (not recognized by earlier versions of linux, and I skipped 9.04 so I don't know if it supports it or not) and be sure to back up.

---

### Post by tgalati4 on 2010-03-28
If you don't need journaling, stick with ext2.  It's been around forever and it's reliable.  You will also gain some space and a slight performance increase without journaling.  Since the files are static, copied once and read many times, you really don't need journaling.

---

