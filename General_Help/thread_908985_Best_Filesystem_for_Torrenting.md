---
title: "Best Filesystem for Torrenting"
date: 2008-09-03
forum: General Help
---

### Post by eternicode on 2008-09-03
I have a small hard drive that I'm going to install for the sole purpose of downloading/holding/seeding torrent files.  What would be the best filesystem for this drive?  Or does it really matter?

---

### Post by Vivaldi Gloria on 2008-09-03
I also have a seperate drive for my heavy amule use. I tried ext3 and xfs for it and I didn't observe any difference. Now I use ext3 because it's more resilient to powercuts/system-crashes than xfs.

---

### Post by gardara on 2008-09-03
ext3 is really stable... But I don't think it will matter that much...
Or well FAT32 doesn't support files bigger than 4gb, so if you're into dvdr, I wouldn't suggest fat32....

But actually the speed of the disk matters more, you can get raptor or sa-sci for maximum speed.

---

### Post by eternicode on 2008-09-03
I have no intentions of using FAT32 :P

My main choice was among Reiser, ext3, and XFS.  I wondered if Reiser might be better because I've heard it works faster with smaller files (thinking about the chunk-downloading method of BT), but I've heard XFS is better for very large files.  But then again, these details are all about file management, so disc speed is probably more important than fs like gardara said.

I think I'll go with ext3, for now at least.

---

