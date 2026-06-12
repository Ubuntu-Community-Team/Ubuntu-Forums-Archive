---
title: "A few question before attempting install"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by Coelocanth on 2006-02-11
Greetings! First post, and I'd like to clear up a few questions/doubts before trying an install:

1) I DLed the AMD64.iso file and burned it to disc. Just wanted to make sure this is the file I need. MY CPU is an Athlon 64 3200+, but is this file intended to be compatible with just the CPU or are there other hardware requirements that will affect it as well?

2) I'm going to be installing it as a dual-boot option on an already existing Windows XP partition. The drive's a Seagate Barracuda SATA drive (250 GB) and was allocated as one complete partition when I installed Windows. Any concerns with installing to SATA drives?

3) I was figuring on allocating 30 GB to the Ubuntu installation. Any suggestions on what would be optimal sizes for the partitions (Primary, swap file, FAT32)?

4) If I want to access files from both the Windows and Linux OSes, they need to be shared through the FAT32 partition, correct? If so, is it a complicated procedure to move a file from Linux to Windows and vise versa (or can this be done at all - the Windows partition being NTFS)?

5) Which file system for Ubuntu? Ext2? Ext3? Something else? Any major considerations/differences between them?

Thanks to any and all who answer. I'm quite looking forward to trying out the Linux OS, so I'd really like to clear up any questions beforehand.

---

### Post by o_fortuna on 2006-02-11
[QUOTE=Coelocanth]Greetings! First post, and I'd like to clear up a few questions/doubts before trying an install:

1) I DLed the AMD64.iso file and burned it to disc. Just wanted to make sure this is the file I need. MY CPU is an Athlon 64 3200+, but is this file intended to be compatible with just the CPU or are there other hardware requirements that will affect it as well?

2) I'm going to be installing it as a dual-boot option on an already existing Windows XP partition. The drive's a Seagate Barracuda SATA drive (250 GB) and was allocated as one complete partition when I installed Windows. Any concerns with installing to SATA drives?

3) I was figuring on allocating 30 GB to the Ubuntu installation. Any suggestions on what would be optimal sizes for the partitions (Primary, swap file, FAT32)?

4) If I want to access files from both the Windows and Linux OSes, they need to be shared through the FAT32 partition, correct? If so, is it a complicated procedure to move a file from Linux to Windows and vise versa (or can this be done at all - the Windows partition being NTFS)?

5) Which file system for Ubuntu? Ext2? Ext3? Something else? Any major considerations/differences between them?

Thanks to any and all who answer. I'm quite looking forward to trying out the Linux OS, so I'd really like to clear up any questions beforehand.[/QUOTE]
1) It'll work fine. AMD64 iso's just need the right processor

2) I used a SATA drive; you should be fine. Ubuntu's partitioner works great, in my experience. (You may want to defrag the NTFS before installing Ubuntu though)

3) Swap file is generally 4GB - Your RAM. So, 1GB RAM = 3GB swap. You obviously don't need that much; I'd recommend about 2.5 GB if you have 512 MB of RAM, 1.5 GB if you have more.

4) It's easy to access (read only) an NTFS partition, and since Ubuntu writes to FAT32 just fine, it's a simple matter of drag and drop (or copy and paste, whichever you prefer)

5) Generally, choose Ext3. It's pretty fast and reliable. Some people have their own preferences, like XFS, ReiserFS, or something else, but there's no need to make complications. Just use Ext3.

---

