---
title: "FAT32 corrupted after Ubuntu wrote to it"
date: 2004-12-09
forum: Hardware &amp; Laptops
---

### Post by Spug on 2004-12-09
Hey there. Ubuntu newbie here. I searched the forum for FAT32 corruption, and while it seems like Ubuntu has some FAT32 issues, I didn't find an answer to my specific question.

I'm dualbooting Windows XP (on a FAT32 partition) and Ubuntu. I keep most of my personal files on the FAT32 partition (such as my music and Opera settings, which I share between my Windows and Linux Opera installations by symlinking). I mount the FAT32 partition in Ubuntu with read and write access. Yesterday I tried to write to it, and it seemed to work like a charm, so I didn't give it any more thought (I used the same /etc/fstab setup in Slackware earlier, so I saw no reason as to why it shouldn't work). However, when I booted Windows today and tried to read any of the files I wrote to with Ubuntu yesterday, Windows told me that the files were corrupted and that it couldn't read from them. I booted Ubuntu again, and there I could read the files in vim, but it said READ ERROR and just displayed lots of garbled gibberish that seemed to come from some of the other files I wrote to in Ubuntu, for some reason. gedit refused to open them and said "I/O error".

Here's my /etc/fstab:

/dev/hda3    /mnt/d    vfat    rw,uid=1000,gid=100    0 0

Does anyone have any light they can shed on this? Perhaps you could post your fstab if you can write to a FAT32 partition like there's no tomorrow? Thanks in advance :)

---

### Post by DyDx on 2004-12-09
/dev/hdb1       /storage        vfat    umask=000        0       0

---

