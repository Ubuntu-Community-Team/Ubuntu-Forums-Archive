---
title: "[SOLVED] Reading and writing from Vista to WUBI Ubuntu"
date: 2008-10-27
forum: General Help
---

### Post by mitchtanz on 2008-10-27
Hi,

I tried to search, but could not find an answer. I know how to read/write out of WUBI Ubuntu and if I have dual boot but is there a way from Vista to a Wubi Ubuntu install? 

I don't expect miracles and will probably install a (?)Ubuntu on this old computer after my new one comes in December. I just want to work with this one Vista+ Wubi Ubuntu.

Mitch

PS The NEW computer will be an (/)Ubuntu + XP for gaming! Bye Vista!

---

### Post by livestockPimp on 2008-10-27
these days I believe there are no problems reading and writing by mounting the windows partition in the linux install (providing Vista still uses NTFS). I have never liked doing that though and normally have a fat32 partition for file storage that both windows and linux can read. From Windows to Linux you can download a ext3 reader and install that, it will allow you to read and write to the linux partitions from Windows.

Hope this helps.

---

### Post by mitchtanz on 2008-10-27
LSP,

Thanks for the answer. Yeap your entirely correct, but WUBI doesn't install as a partition. I tried the 'normal' techniques I knew and could not find a way Vista to read or write to a WUBI-install Kubuntu.

So I'm asking a slightly more complex read/write issue than the normal mount and goes or program download into Vista as I did with XP/Ubuntu. Or I simply missed it!

Thanks for the reply.

Mitch

---

### Post by ago on 2008-10-27
Wubi can r/w within the partition where it is installed (which is ntfs), so any file in there is r/w by both OSes. Any file within the / file system can be accessed by windows using some available ext2 tools for windows. Not sure if such tools support write operations.

---

### Post by mitchtanz on 2008-10-27
ago,

Sorry to be a n00b but "Any file within the / file system can be accessed by windows using some available ext2 tools for windows. Not sure if such tools support write operations." so ext2 CAN read into an WUBI-Ubuntu install? If that is so then I didn't set up the ext2 tool correctly. Normally it gives you an address/mount point ie call this drive [/] etc... So it is different within the WUBI-containing partition from Vista to Kubuntu...

I'll try again--thanks

Best Wishes
Mitch

---

### Post by ago on 2008-10-27
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?)

---

### Post by mitchtanz on 2008-10-27
Thanks ago

How can I access the Wubi files from Windows?
There are a few Windows applications that can mount ext2-based file systems. See for instance: 

•[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) 

•[http://www.fs-driver.org/](http://www.fs-driver.org/) 

The relevant Wubi files you need to access are located under C:\ubuntu\disks\

Another DURRR! read the documentation moment!

Best Wishes
Mitch

---

