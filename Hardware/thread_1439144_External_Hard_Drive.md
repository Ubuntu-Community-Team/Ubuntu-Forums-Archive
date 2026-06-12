---
title: "External Hard Drive"
date: 2010-03-25
forum: Hardware
---

### Post by jlh68 on 2010-03-25
I recently purchased a 320GB 2.5"external HD.  The file system says its owner is root.  Is that how it is supposed to be?  I thought that I would be the owner, sort of like an USB flash drive.

I want to back up to this HD before upgrading my Laptop and desktop computers.

Should I reformat the external HD to a Linux file system or just leave it as a FAT file system?

---

### Post by mikewhatever on 2010-03-25
Can you elaborate on the file system ownership? How does it tell you it's owned by root, especially as fat32 doesn't support permissions?
You'd probably be better off with a Linux file system, unless you are backing up Windows. Keep in mind that fat32 is rather old and doesn't support files over 4 GB.

---

### Post by jlh68 on 2010-03-26
**mikewhatever**W Well I checked the file system using GParted and found that the file system is "ntfs", which the View > File System Support tab shows that it is not supported too well.  

I guess I should reformat the drive to an ext file system.  I am not sure which would be best to use for this drive.  I believe ext3 or ext4 are the newest Linus file systems.

I will be upgrading all of my computers to Ubuntu 9.10 soon in preparation for the 10.04LTS version, which uses ext4.

Do you have a recommendation?  What about my making two (or three) partitions on it, any value to that?

As for the permissions see the screen shot of the file I put on the external drive for testing. The original file on my laptop has me as the owner of the file.

---

### Post by mikewhatever on 2010-03-27
I've done some checking, and apparently, when mounted with <sudo mount...> fat32 is indeed owned by root, so you were right about that. The same applies to ntfs, and the question is, 'Do you mount it by clicking in Nautilus or by <sudo mount...>?'.
As for formatting, it wouldn't hurt, if you don't use Windows. If you do, leave it ntfs, as the support for that file system is rather decent in Linux.

---

### Post by jlh68 on 2010-03-29
What I do is just plug it in (using the USB cable provided) and then click on the drive and then open. So that would be using Nautilus to mount/open. 

I do not use M$ Windows, so I don't care about NTFS as a file system.  I was going to reformat the drive to either _ext3_ or_ ext4_, but I am unsure which would be better for an external drive that mostly would be used for back-up.  That would be back-up of two computers.  

My 40GB HD that I took out of this laptop and put in an 80GB HD. That HD will mount fine and files are owned by me (John) rather than root (although I have no files on it except the test files I just put on it to check it).  Of course the 40GB drive is FAT32 and has 3 partitions (1-Windows OS, 1-Data, 1-restore data to make restore discs).

FYI: the new external HD is ntfs and is a 320GB HD.

---

### Post by coffeecat on 2010-03-29
Ignore the "owned by root" so-called file permission in a mounted NTFS partition. NTFS doesn't support Linux permissions and that owned-by-root is a side-effect of the way the ntfs-3g driver works. You can still read and write as an ordinary user.

---

