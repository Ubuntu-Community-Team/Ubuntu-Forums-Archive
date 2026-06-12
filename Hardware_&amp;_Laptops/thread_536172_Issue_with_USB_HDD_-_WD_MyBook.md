---
title: "Issue with USB HDD - WD MyBook"
date: 2007-08-27
forum: Hardware &amp; Laptops
---

### Post by wreckingcru on 2007-08-27
I have a USB MyBook 250GB drive where I keep all my media. 
I googled to find a tutorial on to make the drive writeable (as it is NTFS). Seemed to work fine initially, and I was able to copy data off the computer's HDD onto the USB drive just fine.

Now, there's a weird problem. I have the drive shared to my Windows laptop using Samba. I wanted to copy some music from the laptop to the share - and the transfer was going fine when suddenly I got an error saying "Out of disk space". That's definitely not true, as there's over 50GB of space there. I figure that there's a problem with Samba.

But, now, even when I try to copy from the local HDD to the USB drive - it either can't do it because of some permissions issue or copies the file over. When it supposedly does copy it over, and I click to access it on the drive, the GUI File manager says "File does not exist". If I initiate another copy process, then it says "File exists, replace?" I say yes, and it won't do it, keeps looping back to the same message again and again. 

I'm guessing something is wrong with the NTFS setup - has anyone else experienced this problem or has any ideas on how to fix it?

---

### Post by raijinsetsu on 2007-08-27
Which NTFS driver are you using? The stock one that comes with the kernel, or NTFS-3g?

---

