---
title: "My Western Digital ide 120gb harddrive wont work. HELP PLEASE"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by zuknivek on 2007-12-17
I have an old ide harddrive. It worked fine when i was using it on a windows computer but then when i installed Ubuntu 7.04 it is write protected all of the sudden. I can view and access all of the files that were still on the hard drive from when i was running windows but i cannot put anything on my hard drive anymore. So now i'm surviving on my 13.5 gb harddrive. Any ideas on how to make my hard drive not write protected anymore? Please help.

---

### Post by crouton on 2007-12-17
Just so I understand you:

You have a 120GB drive that has been used in a Windows machine, and you are attempting to access the files on said 120GB drive using Ubuntu 7.04 (presumably running on the 13.5GB drive).

If this is correct, it sounds like you have the NTFS filesystem on the 120GB drive and you are attempting to write to it using Ubuntu.  Read [this wiki page]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite") for instructions on how to do so.

---

### Post by zuknivek on 2007-12-17
Thank you for the information. Your understanding over the matter is correct. I am currently installing NTFS configuration tool. Hopefully it will work and I will post again after I attempt to fix the problem.

---

### Post by zuknivek on 2007-12-17
My 120gb hard drive is still unusable. I run the program just like the tutorial orders and i still, "Do not have permission to write to this folder." I have no data on the hard drive that i need to keep. If i were to format the hard drive and make it a different partition type would I have the ability to put new files on the drive? If that would work how should i format the drive?

---

### Post by crouton on 2007-12-19
The FAT32 filesystem is read/writable by both Windows and Linux.

---

