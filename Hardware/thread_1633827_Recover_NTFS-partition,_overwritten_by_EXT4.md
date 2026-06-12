---
title: "Recover NTFS-partition, overwritten by EXT4"
date: 2010-11-29
forum: Hardware
---

### Post by alfred2 on 2010-11-29
Hi there,  I have a serious problem:  My external USB-Drive (NTFS 5) was formated with Ubuntu's 'disk utility'. The new format ist EXT4 (with encryption 'on'). Nothing has been written on the drive so far. Ist there any chance, i can revover the data (one big ~25GB 7zipped file) that was stored before on the NTFS volume?  As i can tell, the 'format and encryption' process was to fast (up to a minute), to overwrite the all the data itself, so it should still be 'somewehere'.  So far, i tried with 'testdisk', but it could not find any lost partition (tried quick and deeper search).  Any ideas to get that (very important) file back? Do i have to (somehow) recover the NTFS partition first or will some 'file recovery tools for NTFS' recognize also find files hidden within the new EXT4-format?  Alfred

---

### Post by akand074 on 2010-11-29
Try [photorec]("http://www.cgsecurity.org/wiki/PhotoRec") it is from the same makers of test disk but it actually just searches files and puts them on another partition/hard drive. If you just had the one file then it should be able to find it possibly. Give it a try.

---

### Post by alfred2 on 2010-12-01
photorec did not suceed in finding the lost .7z file (other files, .jpg etc. it found). anyone knows other programms that might do the job?

---

