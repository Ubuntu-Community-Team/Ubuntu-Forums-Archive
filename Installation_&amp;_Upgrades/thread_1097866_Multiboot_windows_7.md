---
title: "Multiboot windows 7"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Mil Doc Jr on 2009-03-16
OK, before I begin let me state a little info about my computer.  I initially started off with Windows Vista, its location is (hd0,0) then I installed Ubuntu 8.10 for dual-boot on (hd,1,0).  Each hd runs approx 110 GB.  I now want to multi-boot with Windows 7 beta 1.  I have 2 externals, a 300 GB WD Passport and a 1 TB WD Essential.  I'm not really wanting to install 7 on either of those due to Windows being a power hog and usb isn't that fast to please me.  If I were to take (hd1,0) and partition it to two 50 GB partitions, leaving Ubuntu on one, the swap on a 5 GB partition, and Windows 7 on the second, would I have any issues in my boot menu?  I really don't feel like spending the time reinstalling everything I have on Ubuntu, and I really want to test out the Windows 7.  Any suggestions, tips, or walkthroughs to keep my computer from hitting the dust would be great.  Thanks.

---

### Post by Mark Phelps on 2009-03-17
From what I've seen, MS Windows (SeVen included) will want to be the first partition on the drive.  So, you could reformat and move your partitions to make the Ubuntu partition the second on the drive.

When you install SeVen, like other MS Windows OSs, it will overwrite the MBR, so if you wrot GRUB to the MBR,  You'll have to replace it.

Also, since you're installing an MS Windows OS after Linux, GRUB most probably will not contain an entry for SeVen, so you will have to manually create that yourself.

However ...  why install the Beta at this late date?  The RC is due out April 10th, and the leaked version of it (build 7057) is already widely available on the internet.

---

