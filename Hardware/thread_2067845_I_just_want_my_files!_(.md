---
title: "I just want my files! :("
date: 2012-10-07
forum: Hardware
---

### Post by thejamesrankin on 2012-10-07
Hi guys,
 
I have a HP 620 laptop running Windows 7. Crashed one day and wouldnt boot up. One of my partitions are corrupt and the MFT is bust. I made a bootable USB of Ubuntu and decided to go about fixing it from there using commands etc. The partition wont mount, nor force mount. Maybe I'm doing it wrong? The partiton is sda2, the file system is NTFS 3, ive being using users as the mount point. There are 44 bad sectors on the disk. Can you give me a list of commands I can try or software. I just want to get access to the drive so I can recover my memories and wipe the disk clean and reinstall Windows.
 
Regards, Desperate 17 year old.

---

### Post by ahallubuntu on 2012-10-07
First thing to try is booting a Windows 7 disc and running chkdsk to try to repair the filesystem.  You can download and burn your own legit copies of Windows 7 discs to boot - google around and find one and burn it to DVD then boot it on your HP.  (Can you boot it from USB?  Not sure, could be.)

After that, you could try booting Ubuntu again and see if you have any better luck.

Understand, though, that if there are bad sectors in files you wanted to save, they are corrupt (gone) forever.  Hard drives can and do fail all the time and when they do, they take their files with them.  That's why it's so important to make backups in case this happens.

---

