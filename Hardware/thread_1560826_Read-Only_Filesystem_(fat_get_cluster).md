---
title: "Read-Only Filesystem (fat_get_cluster)"
date: 2010-08-25
forum: Hardware
---

### Post by ManiacDan on 2010-08-25
I ran into this issue and was able to solve it myself, but it was baffling enough (and not showing up in google) that I thought I should post it here so other people could figure it out without taking 4 hours.

**Symptoms:** My flash drive would randomly fail to access certain files.  After failing to access a file, the flash drive would be locked, with the message "read-only file system."

**Explanation:**  I performed the following:```
dmesg | more
```That showed me the error:
```
[ 1236.588811] FAT: Filesystem error (dev sdc1)
[ 1236.588812]     fat_get_cluster: invalid cluster chain (i_pos 102915494)

```This error means that the file system (FAT32, in this case) is corrupt.  Ubuntu was using the file system just fine in read/write mode until it hit one of the "bad" files (in this case, my Pidgin buddy list).  When Ubuntu encounters a file system error like that, it immediately locks the entire file system in read-only mode for the safety of your data.

**Solution:**  Since the file system is in read-only mode, you can get all your data off it and put it somewhere else.  Copy all the data you can (remember to back up invisible files!) to a safe location

Then go into System->Administration->Disk Utility.  

Select the drive you're having problems with and unmount it

Format it to a more sane file system (like ext4).  

Use the "Check Filesystem" tool to ensure the resulting file system is good (you may need to make sure you're checking physical sectors as well). 

Now, copy all your data back to the drive.  

Congratulations!  Your drive is fixed.

---

