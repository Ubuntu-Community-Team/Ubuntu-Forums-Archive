---
title: "NTFS5: no wubildr on Latitude d810 ( unskilled user)"
date: 2008-08-01
forum: General Help
---

### Post by Ravnos on 2008-08-01
Hi!

I know this error has been reported, but it wasent usefull for me, since i dont have any idea how to move the wubildr to the main partition.

Also, is seam to try to find the wubi in hd0,1 had0,2 and hd0,3.

please, can anyone help me doing it?.
[B]
fstest.exe info c:[/B]
version: 1.0 build 3
part_base: 0x3F (0M)
part_leng: 0x4A852C1 (38154M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000


**fstest.exe list c:**
00000D77    1610612736  pagefile.sys
$BITMAP should be non-resident when in attribute list
ntfs_dir: 18


[B]fstest.exe inode C:\wubildr
fetest.exe comp C:\wubildr[/B]

both gave me this.
$BITMAP should be non-resident when in attribute list
ntfs_dir: 18
 


any idea?

---

### Post by minhmeoke on 2008-08-02
Do you have encryption (Bitlocker) turned on? If yes, then wubi will not work. [http://ubuntuforums.org/showthread.php?t=875570](http://ubuntuforums.org/showthread.php?t=875570)

If you are not using encryption, and wubi still does not work, then you could also uninstall, and reinstall with another target drive.

You can also try defragmenting your hard drive, or using a newer build of grub4dos. 
Download: [http://nufans.net/grub4dos/grub4dos-0.4.4-2008-07-28.zip](http://nufans.net/grub4dos/grub4dos-0.4.4-2008-07-28.zip)
Tutorial: [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)

---

### Post by bean123 on 2008-08-03
I'm sorry, this is one of those corner cases that grldr.mbr can't handle. It would be possible to fix the grub driver, but fix grldr.mbr is not very likely, because it's written in assembly and have serious size limitation. 

If you are using vista, you can try grub2 (although I need to fix the driver first), but if you're using xp, there is no way around it. You need to defrag the partition, or install to another one.

---

