---
title: "Disappearing data on NTFS"
date: 2010-03-11
forum: Hardware
---

### Post by jazzzyjay on 2010-03-11
Hi all, my apologies if this has been covered before, but I have searched high and low for a solution and can't seem to find one.

I am currently running Ubuntu 8.10 (amd64) and wanted to upgrade to 9.10 so decided to do a clean install, seeing as my system is a bit messy now anyway. My Ubuntu system is on ext3 but I also have a 500GB NTFS disk (from Windows days) which I use to store extra data. I wanted to copy some of the files on the ext3 to the NTFS drive in order to back them up before my clean install.

However, after starting the copy using the GUI file browser, some errors came up about not being able to access etc, which I chose to skip, and the copy more or less failed. After this I have been unable to access ANYTHING on the NTFS disk. If i open it in the file browser it says 0 files, 84.6GB free. This implies that the data is still there (disk capacity is 500GB), but Ubuntu is unable to see it. 

I booted into Windows XP and tried to initialise the drive there. A balloon popped up in Windows saying that the location " / " (which I imagine is the NTFS root) is damaged or corrupted, and it advised running chkdsk. I haven't done this yet as I know that chkdsk can often cause extra damage. I went back to Ubuntu and ran ntfsfix, which claimed to be successful but didn't fix the problem. 

I would appreciate if somebody could explain how this happened, and how I might go about fixing it!

Thanks

---

