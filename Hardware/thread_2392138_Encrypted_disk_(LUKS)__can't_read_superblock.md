---
title: "Encrypted disk (LUKS) : can't read superblock"
date: 2018-05-17
forum: Hardware
---

### Post by bricecheptel on 2018-05-17
Hello, 

I have a encrypted (LUKS) Seagate 1 To hard disk. Since I've created the LUKS partition and put my data in it, I can't access it. When I enter the encryption key and try to mount the disk, it says :

Error mounting /dev/dm-3 at /media/me/DISK: can't read superblock on /dev/mapper/luks-d23c323c-c3f2-4d5a-8897-f5ff3a5a26be (udisks-error-quark, 0)

How can I solve it ?

Thanks :)

---

### Post by Autodave on 2018-05-17
I have no knowledge of encrypted drives. However, when I see that error message it almost always means that the HD has died.  It is possible that data got corrupted writing to the super block. If that would be the case, the drive could be reformatted and re-used. However, the data is gone.

There are some programs available for data recovery, but they rarely do much good (if any) and are difficult and time consuming. They rarely work on unencrypted drives, so I would doubt that you would have any luck at all.

Sorry for the bad news.

---

### Post by cpbl on 2018-07-01
Have you seen the answer here: ?

[https://ubuntuforums.org/showthread.php?t=1850713](https://ubuntuforums.org/showthread.php?t=1850713)

It claims to be successful, and sounds the same to me.

---

### Post by oldfred on 2018-07-01
File system with Ubuntu is normally ext4, so you can run e2fsck which is for the ext2, ext3 & ext4 family of formats.

       fsck on encrypted LUKS 
[http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk](http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk) 
            Ubuntu 16.04.3 LTS - correct fsck method for encrypted LVM? 
[https://ubuntuforums.org/showthread.php?t=2375964](https://ubuntuforums.org/showthread.php?t=2375964) 
    
If your encryption key is the part of drive with error then, you may not be able to repair or access drive. Then your previous backups & reinstall becomes only choice.

---

