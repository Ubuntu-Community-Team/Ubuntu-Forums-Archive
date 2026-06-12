---
title: "Ubuntu/vista partitions"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by DannyBlaise on 2009-09-26
I have a quick question I was wondering about. I'm receiving a a new Dell Studio 14z any day now. I plan on doing a dual boot with Ubuntu and vista. My real question is if I left a certain partition of my hard drive for files that would be used between both vista and Ubuntu is that possible? Maybe I'm missing something but it just seems like it could happen. If applicable what format is appropriate? Any help is appreciated. Thank you.

---

### Post by oldfred on 2009-09-26
The question is NTFS or FAT32. Windows will not read ext3 or ext3 although there is a driver you can add that may work, but some say there still are issues.
I have a FAT32 shared partition but I did that 3 years ago when the ntfs driver in linux was not quite reliable, it is now. I would suggest a shared NTFS partition. Ubuntu will also read your windows partition but I do not like writing much data to that partition just in case windows complains. FAT32 will not store a file over about 4GB. I thought I was backing up my Ubuntu to that partition and it always was 4GB. When I changed to an ext3 partiton by backup was much larger, so I never had valid backups until recently.
info on FAT32 and NTFS from Microsoft:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)

---

### Post by MattM11 on 2009-09-26
I currently dual-boot Ubuntu and Vista, with a separate NTFS partition to store documents, pics, music files, etc. on. So it's quite possible.

The only problem you'll have is that the two OSs treat hidden files in different ways. When Vista detects the new partition it dumps a 'System Volume Information' (and sometimes a '$RECYCLE.BIN') folder on it. While hidden in Vista, they'll show up in Ubuntu. You can get round this by creating a text file called ".hidden" on that partition (while in Ubuntu) and writing the (exact) names of any files/folders you want to hide. Then, next time you're in Vista simply right-click ".hidden" and tell Vista to hide it as well. 

Or you could just live with a couple of extra folders on the partition. :)

---

