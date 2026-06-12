---
title: "can't mount western digital 1 tb usb hard drive ubuntu 11.4"
date: 2011-06-23
forum: Hardware
---

### Post by sydox on 2011-06-23
Hello all, I'm still new this it's only my second thread. So if this is already posted or in the wrong place my apologies. I tried a search to see if it was already in the forums but nothing looked helpful.

I have a western digital external usb 1tb hard drive. Model number: wdbaaf0010hbk-01

[http://support.wdc.com/product/download.asp?groupid=120&lang=en](http://support.wdc.com/product/download.asp?groupid=120&lang=en)

It works perfectly on my windows machine but isn't detected on my ubuntu 11.4 machine. In the media drive I have a "floppy" and a "floppy0" I don't have a floppy drive nor do either of those seem to be my hard drive, and my bios DOES recognize the hard drive.

When I first got the hard drive it was in ntsf and I reformatted it on windows to fat 32 I think (maybe it's fat16?). In windows it now shows it as "exfat".

Thanks for your time in advanced.

---

### Post by oldfred on 2011-06-23
If it is exFat it could be a problem. Ubuntu does not have a license and Linux does not license patent pending software. ExFat is intended for flash type devices as I understand the link below. Why not NTFS which is compatible?

[http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)

---

### Post by sydox on 2011-06-24
I originally changed the drive from ntsf because windows 7 has "user permissions". 

So if I used the hard drive on another (windows 7 or vista) computer I wouldn't be able to access my files because I didn't have "administrative permission" or whatever windows calls it (which is the reason I bought it to start with). 

So after reading up on the situation I learned that fat file systems don't have user permissions, thus now I don't have that problem. Perhaps I reformatted it wrong. 

Windows xp didn't give me that problem, although fewer and fewer people are using windows xp, with good reasons.

After reading this I realize it may sound confusing. Bottom line is that I would like to have an external hard drive that would be readable by any machine windows or linux. I have another 2 tb internal hard drive on my windows machine so backing up this external hard isn't a problem if I have to, it's just annoying.

---

### Post by oldfred on 2011-06-24
I am no expert on file systems and windows 7, but we regularly suggest NTFS for shared partitions between all versions of windows & Linux. 

Someone in a windows forum may be able to suggest why you had administrative issues. That is more common in Linux as you have to set permissions & ownership & windows files systems do not support those types of permissions. Most windows uses are full administrators of their systems which is part of the reason for security issues in windows.

---

