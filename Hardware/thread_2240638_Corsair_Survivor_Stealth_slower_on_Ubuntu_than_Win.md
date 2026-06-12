---
title: "Corsair Survivor Stealth slower on Ubuntu than Windows"
date: 2014-08-21
forum: Hardware
---

### Post by U9aOOTQ2WUhm on 2014-08-21
Hey there everyone! I had a question and wanted to know if anyone could help me with it. My Corsair Survivor Stealth 128 GB flash drive is slower on Ubuntu than it is on Windows. Its not the fastest USB 3.0 flash drive in the world but I am happy with the speeds I get on Windows, not so much on Ubuntu. When I copy a single 8 GB .mkv file on Windows I get sustained write speeds of around 90 MB/s but on Ubuntu it peaks at 50 MB/s initially and then quickly drops to a sustained 25 MB/s. Any reason why this is? I don't see any big change when I format the drive to a different filesystem either. I had a hunch that it was because ntfs-3g wasn't as optimized as the drivers in Windows. Any assistance would be greatly appreciated!

---

### Post by Revolutionary101 on 2014-08-21
If an admin sees this could this thread be merged under this account? I accidentally used the wrong email login and unwittingly created an account

---

### Post by oldfred on 2014-08-21
Please just create a post in Resolution Center so an Admin can work with you to remove duplicate account. Dup accounts are not allowed. 

[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

If drive is NTFS or even FAT32 it will not be as fast in Linux. Linux has to reverse engineer the NTFS file system as it gets no help from Microsoft. But if you need compatibility with Windows then you have to use their filesystem.

---

